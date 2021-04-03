# Clean Code - Javascript
## _A brief description of Uncle Bob's clean code book using JavaScript_
---

- [Introduction]()
- [Naming]()
- [Functions]()
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