# Regex Tutorial

In this tutorial you'll learn how a specific regular expression, or regex, functions. We will break down each part of the expression and describing what it does.

## Summary
The following regex will allow you to verify if an email address is valid. 
See the expression below: 
const regex = \b[\w.!#$%&’*+\/=?^`{|}~-]+@[\w-]+(\.[\w-]+)+\b/g;
This regex checks for a prefix and a domain in each address.
In the tutorial below we'll review each part of this regex and what each does.


## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors
The regex begins with the anchor \b
This anchor matches a word boundary position between a word character and non-word character or position.

### Quantifiers
There are several uses of quantifiers in this statement. After each character set we user the + quantifier which matches 1 or more of the preceding set. Since this quantifier is placed directly outside of the chracter set it tells the expression to match 1 or more of the characters in that set. We also require at least one result from the capture group at the end of an address so we use the + quantifier after the capture group as well. See the 4 examples of quantifiers from the statement: 
- [\w.!#$%&’*+\/=?^`{|}~-]+ This requires at least one character from the character set in the prefix
- [\w-]+ This requires at least one character from the character set in the domain. 
- [\w-]+ This requires at least one character after the "." in the capture group at the end of a domain.
- (\.[\w-]+)+ This quantifier requires at least one complete capture group with a "." and a character. If this quantifier were a * instead of a + it would not require at least one complete capture group so an email address would pass even if it looked like this: testemail@gmail

### OR Operator
In our expression we're not using or operators. If in our last group we wanted to specifically look for .com .org or .edu we could get more specific and use an or operator instead of a character class of [\w-]. For our purposes we wanted to keep this expression more flexible and accept any email address provided it follows the baisc pattern. This will better accomodate for international and less common email addresses. 

### Character Classes
1. The first character set is [\w.!#$%&’*+\/=?^`{|}~-] This character set is for the prefix.
In this set has \w which matches any word character. 
The rest of this statement .!#$%&’*+\/=?^`{|}~- defines the other characters that can be included in the email address. 
This set of characters includes an escaped character \/ to specify that the email address can include the character /. 
2. The second character set is [\w-] for the domain. You can see this character set only allows only word characters which are a-z, A-Z and 0-9 and "-" but it doesn't allow all the other charactesr in the characters et for the prefix. 
3. The third chracter set is inside a capture group. It actually matches the character set for the domain [\w-] meaning it only allows for word characters and the "-" but no other characters. 

### Flags
This equation will use the global flag or g. 
With this flag the search looks for all matches, without it – only the first match is returned.

### Grouping and Capturing
The regex ends with a capture group that includes a "." and a character set following the "."
The capture group is as follows (\.[\w-]+)
This checks an email address for something that looks like a .com, .gov, .edu, etc following the domain name.
Don't forget this capture group has a quantifier after it so it will check for at least one instance of the capture group.

### Bracket Expressions

### Greedy and Lazy Match
All of the quantifiers in our expression are Greedy because by default, quantifiers are greedy. This will match as many characters as possible. 
If we added a ? it would make it Lazy which causing it to match as few characters as possible. 

### Boundaries
Our Anchor is a word boundary. This matches a word boundary position between a word character and non-word character or position (start / end of string).

### Back-references
Backreferences are not used in this expression They're designed to match the same text as previously matched by a capturing group. 

### Look-ahead and Look-behind
Our expression does not use look-ahe or look-behind because we don't need to match a group before (look-behind) or after (look-ahead) the main pattern without including it in the result.

## Author
I am Heather Everton, a full stack deleoper attending the U of U Full Stack Software Developer Boot Camp. As a utah native, I enjoy time in the mountains hiking, or paddle boarding and playing with my kids.If you have any questions about the tutorial, you contact me directly at heathereverton88@gmail.com. You can find more of my work at (https://github.com/heather-everton/).