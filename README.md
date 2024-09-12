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

Anchors are used to specify where in the string a pattern must occur to be valid.

Caret (`^`):

Asserts that the match must occur at the beginning of the string.
Example: ^abc matches "abc" only if it appears at the start of the string.

Dollar Sign (`$`):

Asserts that the match must occur at the end of the string.
Example: xyz$ matches "xyz" only if it appears at the end of the string.

### Quantifiers

Quantifiers are used to ensure a certain number of characters or expressions are used a certain number of times

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

We can add some flexibility to our regex with an OR operator, or the `|`.

`/^(http|https):\/\/(www\.)?([a-z0-9-]+\.)+[a-z]{2,}(\/[^\s]*)?$/`

The `|` or the OR operator allows the url in our example to start with `https` or `http`.

### Character Classes

`/^(https?:\/\/)?(www\.)?([a-z0-9-]+\.)+[a-z]{2,}(\/[^\s]*)?$/`

`[a-z0-9-]`:
This character class matches any lowercase letter from 'a' to 'z', any digit from '0' to '9', and the hyphen -. It is used in the part:

`([a-z0-9-]+\.)`: This matches one or more occurrences of valid characters for subdomains or domain names followed by a dot.

`[a-z]`:
This character class matches any lowercase letter from 'a' to 'z'. It is used in:

`[a-z]{2,}`: This ensures that the top-level domain consists of at least two lowercase letters (e.g., .com, .org).

`[^\s]`:
This character class matches any character that is not a whitespace character. The caret ^ at the beginning indicates negation. It is used in:

`(\/[^\s]*)`: This matches a forward slash followed by zero or more characters that are not whitespace, allowing for a valid path in the URL.

### Flags

Flags are used as optional parameters to change the behavior of our regex. For our example, we can make the code case-insensitive by adding a `i` to the end of our expression.

`/^(https?:\/\/)?(www\.)?([a-z0-9-]+\.)+[a-z]{2,}(\/[^\s]*)?$/i`

This modification will allow a url such as HTTps://WwW.gitHub.COM to pass our verification. Depending on your purposes, you may or may not want to use this parameter in your regex for urls.

### Grouping and Capturing

Grouping and capturing allows you to take certain parts of the string and evaluate and manipulate them.

Example:
`/^(https?:\/\/)?(www\.)?([a-z0-9-]+\.)+[a-z]{2,}(\/[^\s]*)?$/`

Grouping:

Parentheses () are used to create groups in regex. Each group can contain one or more regex components.

In the provided regex, the following groups are defined:

`(https?:\/\/)?`: This group matches the protocol part and is optional.

`(www\.)?`: This group matches the "www." part and is also optional.

`([a-z0-9-]+\.)`: This group matches the domain name (including subdomains) followed by a dot.

Capturing:
When you use parentheses to group parts of your regex, the matched content is captured. This means that if you use this regex in a programming language that supports regex capturing (like JavaScript or Python), you can access the matched portions of the string.
For example, if you use this regex to match a URL, you can retrieve the matched protocol, "www." part, and domain name separately from the match results.

Example of Capturing:
If you were to use this regex in JavaScript, you could access the captured groups like this:

`const regex = /^(https?:\/\/)?(www\.)?([a-z0-9-]+\.)+[a-z]{2,}(\/[^\s]*)?$/;`\
`const url = "https://www.example.com";`\
`const matches = url.match(regex);`\

`console.log(matches[1]); // Captured protocol (e.g., "https://")`\
`console.log(matches[2]); // Captured "www." part (e.g., "www.")`\
`console.log(matches[3]); // Captured domain name (e.g., "example.")`

### Bracket Expressions

This bracket expression is used to define a set of characters that can appear in the domain name part of the URL.

`[a-z0-9-]`: This matches any single character that is a lowercase letter (a-z), a digit (0-9), or a hyphen (-).

### Greedy and Lazy Match

Greedy matching means that the regex engine will try to match as much text as possible, while lazy matching (or non-greedy matching) means that it will match as little text as possible.

In our example:
`/^(https?:\/\/)?(www\.)?([a-z0-9-]+\.)+[a-z]{2,}(\/[^\s]*)?$/`

There are no greedy or lazy matching parameters, but we could find some use for lazy matching in a url regex.

Greedy Matching: By default, quantifiers in regex (like `*`, `+`, and `?`) are greedy, meaning they will match as much text as possible. For example, .`*` will match everything until the last possible character that satisfies the pattern.

Lazy Matching: Adding a `?` after a quantifier makes it lazy, meaning it will match as little text as possible. For example, .`*?` will match the smallest amount of text that satisfies the pattern.

### Boundaries

As we have covered in our basic section of regex components, the boundaries in our regex declare that the match must begin at the start of our string `^` and it ends at the end of our string `$`

`^`: This asserts that the match must start at the beginning of the string. It ensures that there are no characters before the pattern.

`$`: This asserts that the match must end at the end of the string. It ensures that there are no characters after the pattern.

### Back-references

In the example `/^(https?:\/\/)?(www\.)?([a-z0-9-]+\.)+[a-z]{2,}(\/[^\s]*)?$/`, we do not use any Back References

As mentioned before, we do use capture groups indicated by the parentheses, but none of those groups are referenced later in the pattern. Backreferences would look like `\1`, `\2`, etc., referring to the first and second capturing groups, respectively.

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
