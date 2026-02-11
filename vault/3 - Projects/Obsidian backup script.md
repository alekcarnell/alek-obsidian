---
collection: projects
date: 2026-02-10
priority: "5"
tags:
  - coding
  - bash
  - homelab
---
# Notes
Working on building an effective backup script for my obsidian vault. 

## Goal
Backup my vault to my NAS and to my external hardrive. 

## Progress

``` bash
#!/bin/bash

#Script to backup contents from Documents/Sync folder to external hardrive. 

# Configuration
SOURCE_DIR="/home/user/Documents/Sync/"
DEST_DIR="/media/user/external_ssd/Sync"
MOUNT_POINT="/media/user/external_ssd"
LOG_FILE="/var/log/backup_script.log"
DATE=$(date '+%Y-%m-%d %H:%M:%S')

# Logging function
log() {
    echo "[$DATE] $1" | tee -a "$LOG_FILE"
}

# Check if mount point exists and is mounted
if mountpoint -q "$MOUNT_POINT"; then
    log "Drive is mounted. Starting backup..."
    
    # Run rsync and log output
    # -a         = Archive, retain file state, permissions, creators, meta data, etc
    # -r         = Recursive
    # --delete   = Delete what wasn't present from source (mirror)
    # --progress = Progress tracker for larger files
    
    rsync -avhr --delete --progress "$SOURCE_DIR" "$DEST_DIR" >> "$LOG_FILE" 2>&1
    
    if [ $? -eq 0 ]; then
        log "Backup completed successfully."
    else
        log "Backup encountered errors."
    fi
else
    log "Drive is not mounted. Backup aborted."
fi

```

SMB file share version with several improvements:

```bash
#!/bin/bash

# Syncs all relevant files from a local directory
# to a Networked Attached Storage (NAS) SMB share.

# == Config ==
SOURCE_DIR="/home/user/Documents/sync/"
MOUNT_POINT="/mnt/NAS"
TARGET_DIR="/mnt/NAS/sync"
LOG_FILE="/var/log/rsync_to_nas.log"
RSYNC_OPTIONS="-avhr --partial --human-readable" #--progress
DATE=$(date '+%Y-%m-%d %H:%M:%S')

# == Excludes ==
EXCLUDES=(
    "--exclude=*.tmp"
    "--exclude=cache/"
)

# Check if NAS is mounted first
if ! mountpoint -q "$MOUNT_POINT"; then
    echo "$DATE [ WARNING ] Mountpoint does not exist. Mounting $MOUNT_POINT..." | tee -a "$LOG_FILE"

    # Make mount point
    sudo mkdir -p /mnt/truenas
    # Mount SMB share to mount point using credential file
    sudo mount -t cifs //192.168.1.1/files /mnt/NAS -o credentials=/root/.smbcredentials,vers=2.1
fi

if  mountpoint -d "$MOUNT_POINT"; then
    # Perform rsync backup
    echo "$DATE [  START  ] Drive is mounted. Starting backup..." | tee -a "$LOG_FILE"
    rsync $RSYNC_OPTIONS "${EXCLUDES[@]}" "$SOURCE_DIR" "$TARGET_DIR" >> "$LOG_FILE" 2>&1

    # Log completion
    echo "$DATE [ SUCCESS ] Backup to NAS completed." | tee -a "$LOG_FILE"
else
    echo "$DATE [  ERROR  ] NAS was not found at $TARGET_DIR and could not be mounted. Operation aborted." | tee -a "$LOG_FILE"
    exit 1
fi
```


# Todo

- [x] Develop an SMB version
- [ ] Forward logs to my email
- [ ] Look for trust signal collapse
- [ ] Verify checksum


# References



