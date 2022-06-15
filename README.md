# Regex Tutorial

In this tutorial, you will learn the fuctions of the regex to match an e-mail.  You can also find this tutorial in a github gist page at:

https://gist.github.com/scarlinj/4048b2221e1899d3a103d912e53fe5b0

## Summary

A regex (regular expression) represents the pattern for e-mail - this is represented by the regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

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

The components of the Regex include a block of meta characters (a range of different characters), followed by the literal character "@", followed by another block of meta characters, followed by the literal character ".", followed by another block of meta characters.  This formatting lets users look for blocks of text that follow a consistent format, without looking for the exact text.  The Regex for an e-mail (such as example@example.com) will look like the below: 

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

### Anchors
Anchors in Regex notation are literal characters that match a position before, after, or between characters.  These allow the search to match e-mails using the "@" anchor.  Regex can use the @ anchor to locate an e-mail and return the string associated with that anchor to the left (beginning after "^" ) and the string on the right (begginning before the anchor "@"), followed by another anchor ".", followed by the end of the address (beginning before the anchor "$").  In the above code, the caret "^" and dollar "$" anchors represent the beginning and end of the address.

### Quantifiers
Quanitifiers specify the number of instances of a charcater, group or class to be included in the input for a match to be found.  These are defined in `{}` in the Regex format.  In the above Regex, the quantifiers "2,6" indicate that there can be between 2 and 6 characters after the "." anchor.  This refers to ".com", ".us", etc.  In other Regex formatting, you may also see " * ", to quantify any character string after the placement of that *.  For example, "domain*" may indicate "domain1," "domain2," "domain55," etc.

### OR Operator

The OR operator indicates that the search will look for either of the qualities adjacent to the "|" notation.  Looking for "abc|xyz" will find anything that either matches "abc" or matches "xyz."  This is not noted in the Regex above.

### Character Classes
The meta-characters are character variables that can fill any character type, such at letters, numbers, or special characters.  The meta-characters in the e-mail are letters `a-z`, numbers `0-9`, and special characters `_\.-`.  These are separated by the anchors "@" and ".".  Anchors are those characters that the expression uses to establish the formatting of the e-mail.  In this case, the Regex searches for the meta-characters to start, followed by an anchor character "@", followed by a group of meta-characters (to establish the e-mail website or service), followed by the anchor ".", followed by meta-characters (to establish the domain, such as ".com" or ".net").

### Flags
Flags are optional features in Regex that allow for advanced functionality.  These can be used separately or together.  In the above Regex, the flag"\d" indicates a decimal digit equivalent to 0-9.

### Grouping and Capturing
Parentheses in the above formatting group the regex between the escaped parentheses `)\`.  This groups the `[a-z0-9_\.-]+`, `[\da-z\.-]+`, and `[a-z\.]{2,6}` as separate groups.  These will represent the e-mail name, host, and domain - name (group1), @ website (group2), .domain (group3).

### Bracket Expressions
We use brackets to indicate a set of character to match.  In the above code, we pair together in separate groups `a-z0-9_\.-`, `\da-z\.-`, and `a-z`.  

### Greedy and Lazy Match
Greedy match looks for as large a match as possible to a given string.  This means that a search will keep looking as long as the search is not satisfied.  This could be "Example*", which will search for all of the strings beginning with example and continuing with anything else.  The above code does not include it, but if we wanted to search for a specific text, followed by anything else (such as all of the "example"s - example1, example2, example 3, etc.) we could use the Regex "example*".

A lazy match will look for as small a group as possible.  It will stop searching once a condition is satisfied.  Adding a quesiton mark "?" at the end of the expression will make the regex search lazy.  For example, "example?" will find "example1" and then stop the search.

### Boundaries
Boundaries in Regular expressions establish where the characters in the address are contained.  As Alan Moore puts it, they are the anchors that are either followed by a word character and not preceded by one or preceded by a word character and not followed by one.  The boundaries ofthe e-mail are established by "()" to group the different components of an e-mail - this includes (name) @ (email) . (domain).  This confines the search to include characters between those word boundaries, to prevent searching for e-mails that may include similar characters to those domains.   For example, "useryahoo@gmail.com" may come up in a search for yahoo.com, even though their user domain is in the gmail website.

### Back-references
We use back-references to match the same text as the text that we just matched in a group, in order to use that string more than once.  These are specified with a backslash and a sub-expression, designated with parentheses ().  By placing parentheses around parts of the regex expression, we group those parts of the e-mails together.  We can then use the back reference The tell the search engine to treat that as an individual item.  In the case of e-mail, we tell the engine to search any combination of letter, symbol or number characters `[a-z0-9_\.-]+)`, followed by `@`, followed by the e-mail domain `([a-z\.]{2,6})`.  We then tell it to match that again and again until it reaches the end of the search.


### Look-ahead and Look-behind
In the future, we can apply this to other common text formats, such as phone numbers and IP addresses.  The above code does not include it, but if we wanted to search for a specific text, followed by anything else (such as combinations of of the "example" - example1, example2, example 3, etc.) we could use the Regex "example*".

## Author

Stephen Carlin is a Coding Bootcamp student in 2022.  He has a background in financial services and is now learning to code.  You can find his github profile at https://github.com/scarlinj.
