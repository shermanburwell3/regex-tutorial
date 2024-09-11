# Regex for the Developer

The purpose of this tutorial is to help aspiring developers understand regex, or regular expressions, in the context of verifying web urls and how to use them in his or her code.

## Summary

In this tutorial, I will be explaining the components and function of a regex for verifying that the user has entered a valid web url.

The following is an example of a regex that verifies that the user's input is a valid web url:

`/^(https?:\/\/)?(www\.)?([a-z0-9-]+\.)+[a-z]{2,}(\/[^\s]\*)?$/`

## Table of Contents

- [Common Anchors in Regex](#comon-anchors-in-regex)
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

We will look at the components in this example:

`/^(https?:\/\/)?(www\.)?([a-z0-9-]+\.)+[a-z]{2,}(\/[^\s]\*)?$/`

`/`: At the beginning and end of the regex, the `/` denotes the boundaries of the regex.

`^`: Asserts the start of the string.

`(https?:\/\/)?`: Matches the protocol part (http:// or https://). The s? makes the 's' optional, and the entire group is optional due to the ?.

`(www\.)?`: Matches the 'www.' part, which is also optional.

`([a-z0-9-]+\.)+`: Matches the domain name, which can consist of letters, numbers, and hyphens, followed by a dot. The + indicates that there can be one or more such groups (for subdomains).

`[a-z]{2,}`: Matches the top-level domain (like .com, .org, etc.), which must be at least two characters long.

`(\/[^\s]\*)`?: Matches an optional path that starts with a slash and can include any characters except whitespace.

`$`: Asserts the end of the string.

### Common Anchors in Regex

Caret (`^`):

Asserts that the match must occur at the beginning of the string.
Example: ^abc matches "abc" only if it appears at the start of the string.

Dollar Sign (`$`):

Asserts that the match must occur at the end of the string.
Example: xyz$ matches "xyz" only if it appears at the end of the string.

### Quantifiers

`?`:
This quantifier means "0 or 1 times." It is used in the following parts of the regex:
(https?:\/\/)?: This means that the protocol (http:// or https://) is optional.
(www\.)?: This means that the "www." part is also optional.

`+`:
This quantifier means "1 or more times." It is used in:

`([a-z0-9-]+\.)+`: This indicates that the domain name can consist of one or more groups of characters (letters, numbers, or hyphens) followed by a dot. It allows for subdomains (e.g., sub.example.com).

`{2,}`:
This quantifier specifies "at least 2 times." It is used in:

`[a-z]{2,}`: This means that the top-level domain must consist of at least two letters (e.g., .com, .org, etc.).

`_`:
This quantifier means "0 or more times." It is used in:
`(\/[^\s]_)?`: This indicates that the path after the domain is optional and can consist of zero or more characters that are not whitespace.

### OR Operator

### Character Classes

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
