# Understanding Regular Expressions (regex)

In this file I will break down a regex into it's core components and explain what each piece is doing and how it functions
to check if any random string is in the format of email.


## Summary

The regex that I will use to demonstrate this is as follows: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
I will explain each piece of this regex and explain how each section functions to identify an email address. 

## Table of Contents

- [Anchors](#anchors)
- [Bracket Expressions](#bracket-expressions)
- [Quantifiers](#quantifiers)
- [Conclusion](#conclusion)


## Regex Components
Because a regex is considered to be a literal it must be wrapped in slashes --> `/ /`
Anything inside those slash marks is the actual regex. Similarly if a `\` is used, any character following the `\` is searched for as
a literal character. This means that `\.` will search for a literal . in a string.

### Anchors
Anchors are found at the beginning and end of any regex and denote the start and end of the literal between the slash marks.
The start anchor is `^` and the end anchor is `$`. Now that we have our regex components and anchors it should look like this --> `/^$/`
Let's continue to fill in this regex till it looks like the one in the above summary section.

### Bracket Expressions
A set of square brackets `([])` is used to represent a range of characters we want to look for and include in our search. In my example regex 
you can see the following: `([a-z])`. This regex will search for any string which contains any combination of lowercase letters a through z.
`([a-z0-9])` <-- this regex will now search for any string which contains all combinations of lowercase letters a through z AND all numbers 0 through 9.
If you used this simple regex in code it would find strings such as "ethan123", "e1t2h3", or "1234welovecode567". It would not return any uppercase letters
or special characters.

### Quantifiers
A quantifier sets the limits of the string that your regex matches. They like to match all occuences of patterns they find. In the case of my example regex,
we can see the quantifier `+` which matches a pattern one or more times. We also see the quantifier `{2,6}` which matches a pattern between 2 and 6 times. 
`\.([a-z]{2,6})` <-- this section of the example regex is looking for a string made up of any lowercase letter a through z that is between 2 and 6 characters long
and has a period before it.
The following examples match this regex search: ".com", ".net", ".tv"

### Conclusion
In conclusion we can now break down the entirety of the example regex.

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

1. `//`<-- this is the container which holds the regex formula

2. `/^$/` <-- next we put in our anchors to denote the start and end of the formula

3. `/^([a-z0-9_\.-]+)$/` <-- next we look for any string containing lowercase letters a through z, any number, and then a few special characters _ . -. The + means
this regex will look for a string which matches this pattern one or more times.

4. `/^([a-z0-9_\.-]+)@$/` <-- next we include a literal @ symbol to find the separation of username and domain name present in all email addresses.
    This regex will now be able to return any of the following in a search: "ethan123@", "1lov3uc1a@", or "stone7@"

5. `/^([a-z0-9_\.-]+)@([\da-z\.-]+)&/` <-- next we need to look for the domain name this email is associated with. For that we use \d to look for any digit 0 through 9,
any lowercase letter a through z, and a period or hyphen.

6. `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` <-- the final piece of this regex is finding a period followed by any lowercase letter a through z which is 2 to 6
characters long. This is the piece that searches for things like: ".com", ".net", or ".gov" at the end of an email address.

7. With all of these pieces in place we can now search for any email address present in a file. Examples include: "greateststudent@ucla.edu", "ethanisnumber1@gmail.com", or "1734catsinahat@yahoo.com"

## Author
My name is Ethan Stone and I am a student in UCLA's coding bootcamp to learn web development. I have a background in game development and plan on using my coding
skills to create websites and make video games. You can find my projects here: https://github.com/RCLobster
