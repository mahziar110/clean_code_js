# Clean Code - Javascript
## _A brief description of Uncle Bob's clean code book using JavaScript_
---

- [Introduction](#Introduction)
- [Naming](#Naming)
- [Functions](#Functions)
- [Commenting]()
- [Formatting]()

## Introduction
---

![img](https://miro.medium.com/max/2100/1*KMHkpT5XmB848a1RUnf30A.jpeg)

You are reading about clean code for two reasons. First, you are a programmer. Second, you want to be a better programmer. Good. We need better programmers.

Learning to write clean code is hard work. It requires more than just the knowledge of principles and patterns. You must sweatover it. You must practice it yourself, and watchyourself  fail.  You  must  watch  others  practice  it  and  fail.  You  must  see  them  stumble  andretrace their steps. You must see them agonize over decisions and see the price they pay formaking those decisions the wrong way.

**Quotes from many computer scientists are quoted in the book, but I (Mahziar Eghdami) think this is the most comprehensive definition of clean code. that Uncle Bob brought in the book.**

> Clean  code  can  be  read,  and  enhanced  by  a developer  other  than  its  original  author.  It  has unit  and  acceptance  tests.  It  has  meaningful names.  It  provides  one  way  rather  than  many ways for doing one thing. It has minimal dependencies,  which  are  explicitly  defined,  and  provides  a  clear  and  minimal  API.  Code  should  be literate since depending on the language, not all necessary  information  can  be  expressed clearly in code alone.
>
> -- <cite> Dave Thomas, CEO of Object Technology International Inc. (formerly OTI, now IBM OTI Labs)</cite>

[⬆️ Back To Top](#Clean-Code---Javascript)

## Naming
---
Names are everywhere in software. We name our variables, our functions, our arguments,classes, and packages. We name our source files and the directories that contain them. Wename our jar files and war files and ear files. We name and name and name. Because we do

**Choosing good names takes time but saves more than it takes. So take care with your names and change them when you find better ones.**

### Use Meaningful Names
**clarity is king.**

**Bad ❌**
```javascript
const a = 'Mahziar';
```

**Good ✔️**

```javascript
const userName = 'Mahziar';
``` 

### Use Intention-Revealing Names
The  name  of  a  variable,  function,  or  class,  should  answer  all  the  big  questions.  Itshould tell you why it exists, what it does, and how it is used. If a name requires a com-ment, then the name does not reveal its intent.

**Bad ❌**
```javascript
// Check that is the user online?
let state = false;
```

**Good ✔️**

```javascript
let isOnline = false;
``` 

### Make Meaningful Distinctions
Programmers create problems for themselves when they write  code solely to satisfy a compiler or interpreter. For example, because you can’t use the same name to refer to two different things in the same scope, you might be tempted to change one name in an arbitrary way.
**If names must be different, then they should also mean something different.**

**Bad ❌**
```javascript
getUsersData();
getUsersInfo();
```

**Good ✔️**

```javascript
getUsersGeneralData();
getUsersDetailsData();
``` 

### Use Pronounceable Names
Humans are good at words. A significant part of our brains is dedicated to the concept of words. And words are, by  definition, pronounceable.

**Bad ❌**
```javascript
const genymdhms;
const modymdhms;
```

**Good ✔️**

```javascript
const generationTimestamp;
const modificationTimestamp;
``` 

### Class Names
Classes and objects should have noun or noun phrase names like Customer, WikiPage, Account, and Address Parser. Avoid words like Manager, Processor, Data, or Info in the name of a class. A class name should not be a verb.

### Method Names
Methods should have verb or verb phrase names like postPayment,deletePage, or save.Accessors, mutators, and predicates should be named for their value and prefixed with get, set.

`Users.getUserName`

`Customars.setPurchaseInfo`

### Don't Use Slang Words
For example, don’t use the name whack()to mean kill(). Don’t tell little culture-dependent jokes like eatMyShorts()to mean abort().
**Say what you mean. Mean what you say.**

### Pick One Word per Concept
Pick one word for one abstract concept and stick with it. for example if you use _district_ word as a concept, and you save the data related to this concept as _district_, don't name it zone in another module.

[⬆️ Back To Top](#Clean-Code---Javascript)

## Functions
---

### Small!
The first rule of functions is that they should be small. **The second rule of functions is that they should be smaller than that.**

**The shorter the functions, the more they help to debug.**

### Do One Thing
_**FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL. THEY SHOULD DO IT ONLY.**_

In the following example, we have a function named setup() that goes through three steps: capture, restructure, and store data.
so this function is doing three things and we should extract it to three functions.

**Bad ❌**
```javascript
setup();
```

**Good ✔️**

```javascript
const appData = getAppDataFromServer();
const organizedAppData = changeAppDataStructure(appData)
setAppDataInLocalStorage(organizedAppData);
``` 

### Function Arguments
The ideal number of arguments for a function  is zero. Next comes one, followed closely by two. Three arguments should be avoided where possible. More than three requires very special justification—and then shouldn’t be used anyway. Arguments are hard. They take a lot of con-ceptual power.

**Destructuring is a good way to avoid this mistake**

### No Side Effects
no side effects. Functions are not allowed to do more than their type definition says. For example, a function that takes an Int and returns an Int cannot change global variables, access filesystem, do network requests, etc. It can *only* do some transformations on the input and return some value.
also Side effects are lies. because Your function promises to do one thing, but it also does other hidden things.

**The function should only work in its own domain**

**Bad ❌**
```javascript
const addNumberToBlackList = (
    blackList, phoneNumberDetails
    ) => {
    const { number, owner } = phoneNumberDetails;
    blackList.push({ number, owner });
}
```

**Good ✔️**

```javascript
const addNumberToBlackList = (
    blackList, phoneNumberDetails
    ) => {
    const { number, owner } = phoneNumberDetails;
    return (...blackList, { number, owner });
}
```

### Remove Duplicated Code
Do your absolute best to avoid duplicate code. Duplicate code is bad because it means that there's more than one place to alter something if you need to change some logic.

Imagine if you run a restaurant and you keep track of your inventory: all your tomatoes, onions, garlic, spices, etc. If you have multiple lists that you keep this on, then all have to be updated when you serve a dish with tomatoes in them. If you only have one list, there's only one place to update!

[⬆️ Back To Top](#Clean-Code---Javascript)


## Comments
---
Nothing can be quite so helpful as a well-placed comment. Nothing can be quite so damaging as an old crafty comment that propagates lies and misinformation.
Comments are not like Schindler’s List. They are not “pure good.” Indeed, comments are, at best, a necessary evil.

The  proper  use  of  comments  is  to  compensate  for  our  failure  to  express  ourself  in code. Note that I used the word failure. I meant it. Comments are always failures. We must have  them  because  we  cannot  always  figure  out  how  to  express  ourselves  without  them, but their use is not a cause for celebration.

### Just Use Comments When You Need
When you find yourself in a position where you need to write a comment, think it through and  see  whether there isn’t some way to turn the tables and express yourself in code.

### Explain Yourself in Code
There are certainly times when code makes a poor vehicle for explanation. Unfortunately, many programmers have taken this to mean that code is seldom, if ever, a good means forexplanation. This is patently false. Which would you rather see? This:

**Good ✔️**

```javascript
const addNumberToBlackList = (
    blackList, phoneNumberDetails
    ) => {
    const { number, owner } = phoneNumberDetails;
    return (...blackList, { number, owner });
}
```

### Don't Comment Bad Code
One of the more common motivations for writing comments is bad code. We write a mod-ule and we know it is confusing and disorganized. We know it’s a mess. So we say to our-selves, “Ooh, I’d better comment that!” No! You’d better clean it! 

### TODO Comments
It is sometimes reasonable to leave “To do” notes in the form of //TODO comments. In the following case, the TODO comment explains why the function has a degenerate implementation and what that function’s future should be.
**TODOs are jobs that the programmer thinks should be done.**

```javascript
try {
    const result = getSelectedThemeByUser(username);
    if (result) {
        const { 
            primary_color, 
            secondary_color,
            icons_json 
            } = result;
        setPrimaryColor(primary_color);
        setSecondaryColor(secondary_color);
        setIconsList(icons_json);
    }
} catch {
    // TODO: Set Default Values 
}
```