# alek-obsidian
My personal do-it-all Obsidian setup. 

## Summary
I went through many iterations, trying just about every system and framework, from PARA to Zettelkasten to +ACEx, before settling into what I have now. 

Based on my experience, what I have found is that the journey for the perfect knowledge management system is fundamentally a dilemma. The user is faced with **two** objectives. 

1. How easy it is to put information into the system
2. How easy it is to get information out of the system

Maximizing any one of these objectives inevitabely minimizes the other. No amount of structure or tooling can give you both. 

## Goals
Based on my personal needs, I found out that I need to lean slightly more into ease of intake rather than ease of output. Too much structure and templating was preventing me from doing work (putting ideas down, doing research, reading and taking notes, etc). I had to find out what the bare minimum was for getting good enough data extraction and then strip away the rest. 

- **Time stamping** somewhere in the structure of the note itself. Frontmatter or Zettelkasten style. (even though files have operating system level time stamps that Obsidian can read, this falls apart if you ever copy your vault and pull from a backup)
- I like to have a **dedicated Projects folder**. 
- I leverage Obisidan **links** for how well Obsidian supports it, but I don't want a Wikipedia as my PKM. That is redundant and clunky.
- I don't use anything with a **calendar**. It's a distraction, I already have a more powerful calendar in my email account, and Daily Notes are mostly useless for productivty. 
- I do find value in having an **inbox** for short term focus. But I do not want any more structure than that (with the exception of the projects folder).

## Structure
My system is set up as follows:

```
alek-obsidian/
├── Inbox 
├── Main Notes
├── Projects
├── Templates
├── Attachments
```

## Workflow

### ├── Inbox
New and unfinished notes go into the Inbox folder. I might keep less than 10 notes floating around in here and I treat them like To-Do tasks. They should be filled in entirely and moved to Main Notes as soon as possible. Obsidian can be configured to automatically place new notes here.  

### ├── Main Notes
Main Notes houses just about everything. I keep about 1000 notes in my live vault all in this one folder with no further organization. To work with older material I rely entirely on search. I find that I do not have any issues with this at all and can find everything that I work on (journal, dream journal, projects, reading, random thoughts, etc) very quickly. 

### ├── Projects
I do allow for further folder creation here to organize projects. I use things like Canvas for projects and find that it's best to keep them in dedicated folders becase (1) there is so few compared to other material in the vault and (2) because canvas's can not have as rich of metadata as a normal .md file. 

### ├── Templates
This is where I store my templates. I only keep a small handful of templates here. Again, the point is to reduce friction. Frontmatter and templates are friction that prevent me from just getting words down. I keep a template for:

- Notes: catch-all for just about anything
- Books: notes on books that I have read
- Dreams: I look back on dreams more than anything so having a separate collection for this helps for analysis
- Videos: notes on interesting videos I have watched. I don't bother with movies because they don't contain anything that a book doesnt already have.
- People: One of my more important templates to link notes, ideas, videos, books, etc back to a person and then be able to have a compendium of that persons corpus.
- Project: Honestly this one may not be necassary but I have it for now. 

### ├── Attachments
An Obsidian-specific addition because of how it handles images and attachments. I would prefer to have them all in one folder rather than floating in Main Notes, since not all attachments will belong to a note in Main Notes. 

## Plugins
This system does not have any dependencies and works with a vanilla Obsidian setup. However I do use exactly 3 plugins. 

- [Templater](https://github.com/SilentVoid13/Templater)
Great and a feature rich way to work with templates, though I keep mine pretty simple
- [Code Styler](https://github.com/mayurankv/Obsidian-Code-Styler)
Purely for aesthetic reasons. I like my scripts to look nice.
- [Notebook Navigator](https://github.com/johansan/notebook-navigator)
Borderline a must-have at this point. I was acheiving a similar functionailty to recent files and multiple pane explorers before by using Bases but this is so much better. 


## Getting Started
1. Download the repo as a .zip or clone the repo.
2. Open with Obsidian.
3. Start creating new notes with templater and check out the database.base file and all of its multiple views.

That's it. I manage my entire PKM with these simple tools and it's been effortless to get information into the system and get it out when I need it. 

Thanks for checking it out!
