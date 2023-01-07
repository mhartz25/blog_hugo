---
title: "NormConf 2022 Notes"
date: "2023-01-02"
menu: "main"
description: "NormConf2022 had some great data talk"

---




I spent part of my holiday going through the backlog of all the great NormConf talks. There were some awesome topics discussed by some great folks in the data community. Tried to compile my notes and figured I'd post them here. I don't have notes for every talk so be sure to check out https://normconf.com/ to find info on all the talks/speakers.

Two themes I found consistent throughout many of the talks:
- Most people are working on very unsexy but super important data work within their companies
- Get really good at the fundamentals, it will make you better at advanced stuff

---


### Group by Statements that Save the Day 
###### by Vincent D. Warmerdam

- it’s unlikely some ML finding will surprise you, Data Visualization findings can surprise you
- what if there are dead chickens in the dataset
- made a library called `doubtlab` for trying to find bad labels in your data
- worry less about “must have skills”, focus on fundamentals
- you can’t get a certificate in common sense and critical thinking
- [https://deon.drivendata.org/examples/](https://deon.drivendata.org/examples/)
    - mentions the above for a checklist before pushing something to prod
- write more TIL blogs

--- 

### Five semesters of linear algebra and all I do is solve Python dependency problems
###### by Tim Hopper

- reflection on his own interests in his career and how they’ve shifted
- your career is unlikely to follow the path you think it will

--- 

### NLP Tip and Tricks 
###### by Lynn Cherny

- recommends UMAP for data exploration
- string_grouprt library can be used for trying to solve string similarity problems

--- 

### How Small Can I get that Docker Container
###### by Matthijs Brouns

- .dockerignore used in a similar way to .gitignore
- `dive` is a tool that allows you to look at what your docker image looks like
- every run statement in your dockerfile creates a new layer in the docker image
    - each layer is essentially a diff of the previous layer
    - you can add and delete stuff in the same run statement to save space

---

### Spark Horror Stories from the Field
###### by Guenia Izquierdo

- modularize your code
- write unit tests
- remove unnecessary code from files that will live in prod
- never had the chance to use spark before, so not much else to add from this talk

---

### Geriatric Data Science: Life after Senior
###### by Luca Belli

- talk is about the IC vs leadership ladder for Data scientists
- IC’s don’t typically get the same level of leadership training as a manager, but there’s still some expectation for them to lead
    - just because you’re an IC doesn’t mean you can ignore leadership development
- the higher you climb the IC ladder the more people will expect management type skills from you
    - should be mindful of this and spend more time training them
    
--- 

### Hack Your Way to a Better API
###### by Zachary Blackwood
- the internals of the software you’re using may be more accessible than you think
- monkey-patching
    - updating or changing code of a piece of software at runtime
- when something isn’t working on imported code, start debugging by looking at its docstring
    - in your IDE this should actually bring you to the file that is being run…you have the ability to change this file if you’d like
    - not best practice to do this at the source level because you’re unlikely to document it and it will disappear when you update your packages
    - other option is to write your new, desired function within your own file that overwrites the old function
- the develop tools that you find in chrome can also be found in many apps you use, including VScode
- uses a website called [curlconverter.com](http://curlconverter.com) to format cURL commands to the language/library of your choice

---

### What’s the simplest possible thing that might work, why didn’t you try that first?
###### by Joel Grus

- his favorite question to ask
- in 2022 implementing bert models can be simple, even though the model is more sophisticated than Logistic Regression or Naive Bayes
- as our tools get better the boundary between complex and simple changes
- people create systems that abstract away complexity, this is different than dumbing something down
- think about ways to abstract complexity away from things you are often doing
- simplicity is something we only discover through experience and with confidence
    - simplicity is not the sign of a newbie

---

### It’s all about cost: How to think about Machine Learning Products
###### by Peter Sobot

- engineering is about building the best thing you can given the constraint of the problem

---

### ML doesn’t always replace rules, sometimes they work together
###### by Jeremy Jordan

- Traditional approach for ML
    - first deploy a heuristic approach
        - Rules based approach
        - e.g. for a spam filter you can give it specific words to look for. Then as time goes on you can monitor user-behavior to see how they might label messages as spam or pull messages out of the spam folder
    - once you have labelled data you can take a more ML approach
- rules plus ML can give you much greater results than either approach used independently
- combine the two systems in a policy layer
    - could be as simple as an OR statement. i.e. if one system evaluates to True then take that
- have an evaluation set that you can use to more easily test versions of your system against

---

### All my machine learning problems are actually data management problems
###### by Shreya Shankar

- most ML failures exist outside of whatever business logic that is running ML algos
- assumptions that exist in dev/training do not always translate to production
- telemetry from prod systems is important

---

### Ethan Rosenthal and the M1 misadventure
###### by Ethan Rosenthal

- has a medium article talking about managing python env for DS
- my take away is, python dependencies and environment management are such a mess, believe it or not
- reproducibility of an environment is important. If you need to revisit an analysis from 6 months ago, you should be able to have it up an running easily

---

### Data is the new coffee
###### by Peter Baumgartner

- talks about practices for annotating data for data science purposes
- calibration and agreement
    - each of your annotators should be on the same page for what each criteria or label means
    - how often multiple people agree to give the same case the same label is important
    - want to have annotation guidelines that give people some structure on what to do
- as you encounter more data it is normal to see your annotation task drift a little bit
    - don’t expect to get it right the first time
- you don’t necessarily need to limit your annotation task to a subset of domain experts
- it will take iterations until you get everyone on same page and your annotated dataset becomes “gold” level
    - “it’s going to take longer than you think”
- having a correlation amongst annotators at .9 and above is very rigourous

---

### How to Translate to PM speak and back
###### by Katie Bauer

- early on would give PMs too much detail, which they didn’t seem to like
- “assume good intent”, believe that you and the person you are working with have each other’s best interests at heart
    - she later amended this to “assume good intent, but consider incentives”
- product managers speak a language of progress
- most questions PMs ask you are implicitly causal.
    - Focus your work on things they can control
    - prioritize logical consistency over being technically correct
    - describe your results as inputs and outputs
- plan your work according to their positioning
    - while not all environments are going to be cutthroat, PMs are inherently competing with other PMs
- accept that no translation will be perfect
- your suggestions will more be used as guardrails, rather than taken as bible
- pick your battles when you try to apply a lot of rigor to a situation, should be when stakes are high
- arming PMs with data that they can take and apply to a different context can be valuable in helping them be bought into the idea of data
- she likes a hub and spoke style data team structure

---

### Tracer Bullets and Working Backwards: Simple Frameworks for Solving Problems
###### by Caitlin Hudon

- premortems are a good way to tackle known unknowns
    - can do on your own or ask SMEs questions to fill out this framework
- Tracer bullets can be used in the unknown unknown domain
    - they give real time feedback
    - use minimum amount of code to get code to next step of project
    - different from a prototype, because tracer bullets are more of an along-the-way, iterative process
    - expounded on further in the book “the Pragmatic Programmer”
- overall goal is to use frameworks to increase the amount of feedback you are getting throughout all stages of development
- also recommends the book “Thinking in Bets” by Annie Duke

---

### Building an HTTPS Model API for Cheap
###### by Ben Labaschin

- we do not have enough time
- weigh the trade-offs of your tools before choosing software
- normy software
    - reliable
    - an investment
    - easy to learn

---

### Data’s Desire Paths
###### by James Kirk

- best way to think about Recommender systems is as a desire path
    - a desire path describes the phenomena of not putting down a walkway on a college campus until you see the path people take to cut across the grass
- a healthy recommender project has
    - clearly defined users
    - a measurable definition of success
    - a clear relationship between recommender success and business success
    - data and a tech stack ready to implement and iterate on recommendations
- types of recommendations:
    - basic recommendations
        - you are webpage X so we will point you towards webpage Y
    - personalization
    - omakase
        - “hey alexa, play music”
- don’t be afraid to pre-calculate recommendations as you scale up
- recommends a book by Kim Falk for intro to recommenders

---

### The Zen of Tedium
###### by Brandon Rohrer

- you only have so many hours to be productive within a day
- there are trade-offs for doing things the hard way vs automating vs doing tedious work

---

### How should I represent the intermediate thing?
###### by Brianna McHorse

- data structures are clear at the beginning and end, but things are less clearly defined in the interim
- care about performance later. You can only do so many things at once
- Heuristics for choosing data structures
    - dict: I am a human with a human brain
    - defaultdict: I am a human and i want to add things as i go
    - class: I am a human and I’m very sure about what’s going into this object
    - list: I have several things, i want to sort them, and I don’t mind if they change
    - tuple: I only have a few things, they’re not going to change, I don’t need to access them
    - namedtuple: ??? maybe if things really need to be immutable
        - most cases can just use a dict
        
---

### I’d have written a shorter solution but i didnt have the time
###### by JD Long

- tells a story about some study where people’s only thought was to add something, until they were prompted that removing something is an option too
    - additive ideas come to mind quickly, but subtractive ideas require more cognitive effort
    - e.g. if you give someone a recipe and say how do we makes this better, almost no one will attempt to remove something
- the MVP model is a subtractive priming prompt
- writing a reproducible example(reprex) is a critical tech skill
    - minimum reproducible example
    - reprex debugging is akin to rubber duck debugging
    - helps to remove noise of other things involved and isolate to just what your problem is
- don’t try to boil the ocean, build things thrice
    - first time there’s bugs, second time you can avoid them, third time is when you make it pretty
- on his team of analysts the top 2 success criteria are 2 sides of the same coin
    - ask a lot of questions
    - don’t try to fake it if you don’t know it

---

### Just use one big machine for model training and inference
###### by Josh Wills

- be careful at what you get good at
- using one big machine is a paradigm strategy for keeping things simple
- `htop` is a unix tool to see underlying process running on machine
    - can combine with `tail`
- he is a DuckDB enthusiast

---

### Data Driven Promotions
###### by Rose Wiegley

- using data to move up in your corp
    - what matters?
        - make a responsibility matrix, if your company doesn’t already have anything like this
            - idea of proving you are already doing the next level’s job before being promoted
    - track progress
        - keep an ongoing brag document
            - organize it by the same categories that are in your responsibility matrix
            - should be your map of where you are and where you need to go
            - be proactive about this
    - frame your review
    
---

### Don’t Do Invisible Work
###### by Chris Albon

- record your work and tell people about it
- if you don’t consciously spend time to track your work, you will never remember it and it will be forgotten
    - if it’s not remembered it’s like it never happened
- no one is going to do this for you
- work that tends to be invisible
    - mentorship
    - ad-hoc work
- he just uses an activity log. Keeps a text file open all day and write a bunch of one line entries
    - dump in anything that might be useful
- the goal is if someone asks your boss what you did/do, they have a deep well of concrete examples to choose from