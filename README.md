<h1 align="center"> <a href="https://gist.github.com/Lorena-RM/c9a3599457503cdd5f468c10187865ff">
Regex Tutorial 💻</a>
</h1>

<p align="center"> Regular Expressions create a unique filter for various patterns of text that we can actually use pretty regularly. <a href="https://coding-boot-camp.github.io/full-stack/computer-science/regex-tutorial">Regular expressions, or regex for short, are a series of special characters that define a search pattern.</a> In the madness of those expressions, (regex) that to someoene who is unaware of regular expressions would look like gibberish, is a complex search pattern that can be used in documents, javascript, python, or anyhting you can possibly search for in any type of document. As you read through this, you will be able to familiarize yourself with regular expressions, and be able to implement it in your intended use for coding or just as a <a href="https://youtu.be/7DG3kCDx53c?t=60">tool for yourself in a text editor for writing or find and replace.</a></p>

<h2 align="center">Summary</h2>

The Expression **below** is **only** an example! This expression in particular would allow us to search for phone numbers in just about anyway you can write them, in other words can find various patterns in various different ways!
<div align = "center" markdown="1">

```
(?:(\+1)[ -])?\(?(?<areacode>\d{3})\)?[ -]?(\d{3})[ -]?(\d{4})
```

The Expression above would search for numbers like these:


```
1234567890
123-456-7890
123 456 7890
(123) 456-7890
+1 123 456 7890
etc...
```

Web Dev Simplified provide a short detailed explination video on this expression above (<a href="https://youtu.be/rhzKDrUiJVk">Learn Regular Expressions In 20 Minutes</a>)
</div>

For this Tutorial, I would be defining and using expressions to familiarize ourselves with Regex and using this Expression:

```
/^[a-zA-Z0-9_\.-]+@[\da-zA-Z\.-]+\.[a-zA-Z\.]{2,6}$/
```

as an example of how Regex can be used to find and match an Email! 

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)
- [Resources](#resources)

## Regex Components

#### The Expression:
```/^([a-zA-Z0-9_\.-]+)@([\da-zA-Z\.-]+)\.([a-zA-Z\.]{2,6})$/```

This search pattern is meant for complex **email** validation. It checks to see if a string fulfills the requirements and matches for an email. As you read through this, we will dive in more detail throughout this tutorial as you read on. for the moment, this is the breakdown for this pattern.

#### /**```^([a-zA-Z0-9_\.-]+)```**@([\da-zA-Z\.-]+)\.([a-zA-Z\.]{2,6})$/
In the first part of this search pattern:

* The string can contain any lowercase or uppercase letter between a-z

* The string can contain any number from 0-9

* The string can contain an underscore, period, or a hyphen

* The string can match the pattern multiple times

#### /^([a-zA-Z0-9_\.-]+)**```@```**([\da-zA-Z\.-]+)\.([a-zA-Z\.]{2,6})$/
In the second part of this search pattern:

* The string matches the '@' character

#### /^([a-zA-Z0-9_\.-]+)@**```([\da-zA-Z\.-]+)```**\.([a-zA-Z\.]{2,6})$/
In the third part of this search pattern:

* The string can match any digit character (0-9) ('**\d**')

* The string can contain any lowercase or uppercase letter between a-z

* The string can contain a period or a hyphen

* The string can match the pattern multiple times

#### /^([a-zA-Z0-9_\.-]+)@([\da-zA-Z\.-]+)**```\.```**([a-zA-Z\.]{2,6})$/
In the fourth part of this search patterm:

* The string matches a '.' character

#### /^([a-zA-Z0-9_\.-]+)@([\da-zA-Z\.-]+)\.**```([a-zA-Z\.]{2,6})$```**/
In the fifth and final part of this search pattern: 

* The string can contain any lowercase or uppercase letter between a-z

* The string can contain a period or a hyphen

* The string can match the pattern multiple times

* The string must be between 2 and 6 characters.

### [Anchors](#table-of-contents)

Anchors don't really specify a character search in particular. Instead, using an Anchor expression actually searches and refers on the position of the given character group set with the anchor type you use.

Using our search pattern in this tutorial, the beginning of the search pattern is 

```
^([a-zA-Z0-9_\.-]+)
```
Notice the carrot character **'^'**. That beginning carrot anchor followed by the first character set is what regex searches for at the **start** of the qualifing match in our search pattern.
```
([a-zA-Z\.]{2,6})$
```
This is the same for the **'$'** dollar character Anchor however, it caputures the **end** position of the desired match in your search pattern

<p>Below is a screen shot example of an expression with <b style='color:red'>no anchors</b>. using <a href="https://regexr.com/">RegExr</a>, This search pattern is matching <b style='color:red'>all occurances</b> of the capturing group.</p>

<img width="1387" alt="Screen Shot 2022-10-14 at 1 41 37 AM" src="https://user-images.githubusercontent.com/106778363/195792489-df0c8150-3081-4a4f-bebf-aff3f71f2f86.png">

This new example is the same expression with the '^' carrot anchor added to the beginning of the search pattern. Notice how it matches <b style='color:green'>only the FIRST occurance of 'Hello'</b>.

<img width="1387" alt="Screen Shot 2022-10-14 at 2 06 03 AM" src="https://user-images.githubusercontent.com/106778363/195795597-c02ba6a2-d305-45df-9fc7-6b6fe3b05ace.png">

This final example is the same expression with the '$' dollar anchor added the end of the search pattern. Notice how it matches <b style='color:green'>only the LAST occurance of 'Hello'</b>

<img width="1387" alt="Screen Shot 2022-10-14 at 2 09 30 AM" src="https://user-images.githubusercontent.com/106778363/195796240-763600c4-cc04-4b71-9173-738b6dd7375f.png">

### [Quantifiers](#table-of-contents)

Think of Quantifiers more like the rule setters. these metacharacters basically set a rule of how many occurances it can have inside of a character, group, or character class in a string. This sets a rule to the character, group, or character class thats right before the quantifier character.

this table is an example of the basic most common characters used in regex.

<center>

|symbol|Name|quantification of previous character|
|:----|:----:|----:|
|? |Question Mark|optional(0 or 1 repititions|
|*|Asterisk|Zero or more times|
|+|Plus Sign|one or more times|
|{n,m}|curly braces|between n and m times|

</center>

In our follwing search pattern for the Tutorial you'll notice that it has 3 instances of a quantifier:

/^([a-zA-Z0-9_\.-]```+```)@([\da-zA-Z\.-]```+```)\.([a-zA-Z\.]```{2,6}```)$/

The '+' Plus sign character we used in the first 2 occurances of this search pattern captures the charactter class right before it and searches for that pattern and can match one or more times in characters.

The '{2,6}' curly braces characters used in the 3rd occurance of the search pattern will look for that pattern but limit the amount of characters to a certain amount only for example, in our tutorial search pattern the charcter class that is captures is going to be ```[a-zA-Z\.]``` because it is right behind the quantifier. which means it look for strings that have any letter (lower or uppercase) and period characters but will _limit_ the string between 2 to 6 chars. Therefore anything under 2 characters or anything above 6 chars will NOT be a match. 

### [Grouping Constructs](#table-of-contents)

Groups serve a great purpose for find and replace especially if its a specific part of the search pattern you want to isolate from your whole search pattern. or just separate your search pattern into different recognizable groups of your own prefrence.

Take our **own** tutorial search pattern

```
Group 0: /^([a-zA-Z0-9_\.-]+)@([\da-zA-Z\.-]+)\.([a-zA-Z\.]{2,6})$/

Group 1: ([a-zA-Z0-9_\.-]+)

Group 2: ([\da-zA-Z\.-]+)

Group 3: ([a-zA-Z\.]{2,6})
```

now lets take away the parenthesis from groups 1, 2, & 3 

```
Group 0: /^[a-zA-Z0-9_\.-]+@[\da-zA-Z\.-]+\.[a-zA-Z\.]{2,6}$/
```
Our ***NEW*** search pattern with NO parenthesis to capture any groups is still a valid search pattern. However, The ***ONLY*** difference is that instead of capturing groups 1,2, & 3 we **only** caputure group 0, which is the WHOLE expression in itself. Like the example below using my email as test, you'll notice that the only group captured was match 0 which is the whole expression:
<img width="1381" alt="Screen Shot 2022-10-19 at 3 13 35 PM" src="https://user-images.githubusercontent.com/106778363/196805645-847598e6-fbbc-45f5-9065-46719de92f95.png">
***However*** if we add those parenthesis back to isolate our capturing groups, we are given more groups that hold specific parts of the search pattern that we want to isolate.

<img width="1381" alt="Screen Shot 2022-10-19 at 3 13 11 PM" src="https://user-images.githubusercontent.com/106778363/196806833-31e410e7-d156-4537-b220-bfadd5451dc3.png">

If in any case we want to replace say for example group #1 in our tutorial search pattern to '*' grouping constructs would allow us to replae that snippet while keeping the rest of that search pattern the same.

Brad Garropy demonstrates a short tutorial for [regex find and replace](https://youtu.be/xMhKstbdr3k). More importantly this also gives a great example on grouping contructs and how we can use them to replace new values into them!

### [Bracket Expressions](#table-of-contents)

Bracket expressions can be used to search for certain characters to match regardless the size of the string. [Anything inside a set of square brackets ([ ]) represents a range of characters that we want to match](https://coding-boot-camp.github.io/full-stack/computer-science/regex-tutorial). In the most basic example to best understand bracket expressions, if my bracket expression had a single character of 'a' (a.k.a. [a]) then the following examples would match "aaa", "pan".

Using [RegEx](https://regexr.com/) for this example, you'll see the characters inside of the bracket expressions will search for any of those single characters I gave it inside of the bracket expressions.

<img width="1387" alt="Screen Shot 2022-10-17 at 6 54 40 PM" src="https://user-images.githubusercontent.com/106778363/196312098-f873a65e-8b9e-40cf-8ba2-a309fcc9ae58.png">

adding a '-' hyphen character inbetween certain characters will create a range of those possible characters between those 2 chosen alphanumeric characters.

<img width="1387" alt="Screen Shot 2022-10-17 at 7 21 46 PM" src="https://user-images.githubusercontent.com/106778363/196313915-d36e5b99-8fb1-4d58-81e7-00798bfed455.png">
<img width="1391" alt="Screen Shot 2022-10-17 at 7 21 59 PM" src="https://user-images.githubusercontent.com/106778363/196313967-c06e4eec-d3df-404a-aeca-e1154c342671.png">


<center> The table below provided by <a href="https://www.ibm.com/docs/it/netcoolomnibus/7.4?topic=library-bracket-expressions">ibm</a> gives a short simple description of how bracket expressions can be used</center>

<center>

|Expression|Description|
|:----|:----:|
|[abc] |Matches any character in the square brackets|
|[a-d]|Matches any character in the range of characters separated by a hyphen ( - ).|
|[^abc] [^a-d]|Matches any character except those in the square brackets or in the range of characters separated by a hyphen ( - ).|

</center>

In our tutorial regex, there are quite a few examples to look at and understand:

/^(```[a-zA-Z0-9_\.-]```+)@(```[\da-zA-Z\.-]```+)\.(```[a-zA-Z\.]```{2,6})$/

knowing the information from above in addition characters such as '.' periods or '_' underscores or '-' hyphens and also be included inside of bracket expressions.

### [Character Classes](#table-of-contents)

character classes are like defined groups regex has that we can use in our search patterns for example in our tutorial search pattern, we use one instance of a character class 

/^([a-zA-Z0-9_\.-]+)@([```\d```a-zA-Z\.-]+)\.([a-zA-Z\.]{2,6})$/

the character class '\d' is equivelent to [0-9] if it was used in a bracket expression.

below using [RegEx](https://regexr.com/) gives a few examples of some common character classes that can be used in regular expressions.


### Character: **'.'**:
![dotChar](https://user-images.githubusercontent.com/106778363/196326078-62385169-d2c4-4b38-8fb8-7eb440189b9f.gif)

### Character: **'\d'** & **'\D'**:
![char d](https://user-images.githubusercontent.com/106778363/196326627-bd784fa4-9e3d-4fc9-a04a-7af8c2ad2660.gif)

### Character: **'\w'** & **'\W'**:
![char w](https://user-images.githubusercontent.com/106778363/196326785-ccf4e7dc-ca98-4ca3-b6cf-abefa52f0651.gif)

### Character: **'\s'** & **'\S'**:
![char s](https://user-images.githubusercontent.com/106778363/196326929-6251874a-b468-45b2-b41f-72aa60327cfb.gif)

### [The OR Operator](#table-of-contents)
Although the OR operator is not being used in our tutorial search pattern we can breifly still go through it with other examples!

As simple as it gets, the OR operator uses the '|' character to include 2 different options you give the search pattern and match one OR  the other.

<img width="1387" alt="Screen Shot 2022-10-16 at 9 34 43 PM" src="https://user-images.githubusercontent.com/106778363/196328095-ad235445-f4e2-471e-b4e4-e22ca7af4dd1.png">

> FYI: Regex expressions are also case sensitive!
### [Flags](#table-of-contents)

There are penty of ways we can use regex inside of a search pattern for desired results but Flags can be used on the outside and still have some effect on youre results!

Flags can be placed on the outside of your regex search pattern outside of the second slash that wraps the search pattern. This allows for more additional "filters" depending on what your are searching for or how you are searching it.

using our tutorial search pattern flags can definetly be implemented in our searches. Lets say for example we have a list of emails and want to match the valid ones:

![flagsGif](https://user-images.githubusercontent.com/106778363/196742158-21848b95-fbf7-4f33-9183-4a2556158e17.gif)

This exmaple GIF above indicates multiple flags that can be placed and have it effecting our matches!

<center>

|Flag|Name|Description|
|:----|:----:|:----:|
| i |ignore case|<a href="https://regexr.com/">Makes the whole expression case-insensitive. For example, /aBc/i would match AbC.</a>|
|g |global|<a href="https://regexr.com/">Retain the index of the last match, allowing subsequent searches to start from the end of the previous match. Without the global flag, subsequent searches will return the same match.</a>|
|m|multiline|<a href="https://regexr.com/">When the multiline flag is enabled, beginning and end anchors (^ and $) will match the start and end of a line, instead of the start and end of the whole string.</a>|
| u |unicode| <a href="https://regexr.com/">When the unicode flag is enabled, you can use extended unicode escapes in the form \x{FFFFF}.</a>|
|y|sticky|<a href="https://www.codeguage.com/courses/regexp/flags">Makes the expression start its searching from the index indicated in its lastIndex property.</a>|
|s|single Line(dotall)|<a href="https://regexr.com/">Dot (.) will match any character, including newline.</a>|

This table gives un plenty of information from a couple resources to help us identify what each flag does to our search pattern.

</center>


### [Character Escapes](#table-of-contents)
as you have learned so far we can use our symbols as quantifiers in someinstances but what if we want to actually search a symbol in our search pattern? 

Character Escapes are use to capture that very aspect of searching for specific special characters. take for example searching the '.' period charcater can be searched using out.

<img width="1381" alt="Screen Shot 2022-10-19 at 12 05 21 PM" src="https://user-images.githubusercontent.com/106778363/196770149-f5303d4f-0d27-4ec6-a828-5c0e8c98ae63.png">

using [RegEx](https://regexr.com/) yet again to create an example for you all you can see in the above screenshot I have created a character set that captures any of the 2 escaped characters embedded inside of the character set. there for not viewing the '$' dollar sign as an anchor but has a character to search for. like wise for the period character.

our **own** tutorial search patter also has some instances of character escapes:

1. /^([a-zA-Z0-9_``\.``-]+)@
2. ([\da-zA-Z``\.``-]+)
3. ``\.``
4. ([a-zA-Z``\.``]{2,6})$/

## [Resources](#table-of-contents)
These Resources made this Gist possible, feel free to hceck them out! 📖

* [RegEx](https://regexr.com/) 
* [Learn Regular Expressions In 20 Minutes](https://www.youtube.com/watch?v=rhzKDrUiJVk)
* [Regular Expression Tutorial:matching a username](https://coding-boot-camp.github.io/full-stack/computer-science/regex-tutorial)
* [Intro to regular expressions](https://youtu.be/7DG3kCDx53c)
* [Bracket Expressions](https://www.ibm.com/docs/it/netcoolomnibus/7.4?topic=library-bracket-expressions)
* [2.4: Regular Expressions: Capturing Groups - Programming with Text](https://youtu.be/c9HbsUSWilw)
* [regex find and replace](https://youtu.be/xMhKstbdr3k)
* [some examples using our Tutorial Regex!](/regex.js)



## [Author](#table-of-contents)

Take a look at some other work ive done on my repos from my Github:

* Github: [Lorena-RM](https://github.com/Lorena-RM)

Get in contact with me Directly within linkden or my personal email:

* Linkden: [Lorena Morales](https://www.linkedin.com/in/lorena-morales-496855240/)

* Email: [lorenarm.999@gmail.com](mailto:lorenarm.999@gmail.com)