# Matching a URL with RegEx

Regular expressions, or regex, are useful tools for pattern matching and data validation. While they may look like a jumbled mess at first glance, each component of a regular expression has a specific purpose. For this deep dive, I will be reviewing the following expression:

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`. 

## Summary

The provided regex pattern is designed to match URLs. It can handle both HTTP and HTTPS protocols and supports domains with various lengths and extensions. The pattern incorporates several different  regex elements such as anchors, quantifiers, character classes, grouping, and more. I will review each component of this regex to gain a better understanding of what it is actually doing.

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

The `^` and `$` symbols are anchors used to match the start and end of a line, respectively. In this regex, they ensure that the entire string is matched from start to finish.

### Quantifiers

The `?` quantifier makes the preceding group or character optional. In this regex, it is applied to (https?:\/\/) to allow for URLs without the protocol (http:// or https://).

The `*` quantifier matches zero or more occurrences of the preceding group or character. It is used with `([\/\w \.-]*)` to handle any additional path or query parameters in the URL.

### OR Operator

The `|` symbol functions as an OR operator, allowing a choice between two patterns. It is not used in this regex pattern.

### Character Classes

`[\da-z\.-]`: This character class matches any alphanumeric character `(\d)`, lowercase letter `(a-z)`, period `(.)`, or hyphen `(-)`. It is used to match the subdomains or domain prefixes.

`[a-z\.]`: This character class matches any lowercase letter or period. It is used to match the domain extension.

### Flags

Regex flags are not used in this pattern. Flags modify the behavior of the regex matching, but none are specified here.

### Grouping and Capturing

`(https?:\/\/)`: This group matches the optional protocol (http:// or https://). The colon `(:)` and double forward slashes `(//)` are escaped using backslashes.

`([\da-z\.-]+)`: This group matches one or more alphanumeric characters, lowercase letters, periods, or hyphens. It captures the subdomain or domain prefix.

`([a-z\.]{2,6})`: This group matches the domain extension, which consists of two to six lowercase letters or periods.

`([\/\w \.-]*)`: This group matches the path and query parameters. It can contain forward slashes, alphanumeric characters, spaces, periods, or hyphens.

### Bracket Expressions

The bracket expressions in this regex pattern include character classes. They are used to define the range of characters that can be matched. The following bracker expressions are present:

`[\da-z\.-]+`: Matches one or more occurrences of characters that can be digits (\d), lowercase letters (a-z), dots (.), or dashes (-). This is used to match the subdomain or domain name part of the URL. For example, it matches www or example in www.example.com.

`[\/\w \.-]*`: Matches zero or more occurrences of characters that can be forward slashes (\/), word characters (\w), spaces ( ), dots (.), or dashes (-). This is used to match the path elements in the URL. It allows for alphanumeric characters, certain symbols, spaces, and dots in the path. For example, it matches /path/to/file in https://www.example.com/path/to/file.

### Greedy and Lazy Match

In this pattern, the `*` quantifier after `([\/\w \.-]*)` allows for zero or more occurrences of characters in the path. The `*` is greedy, so it will match as many characters as possible while still allowing the pattern to match the entire URL. This means it will consume all available characters in the path before considering the following part of the pattern.

### Boundaries

Boundaries are not used in this regex pattern. Boundaries help define the limits of a match, but they are unnecessary here.

### Back-references

Back-references are not used in this regex pattern. Back-references allow referencing previously captured groups within the pattern.

### Look-ahead and Look-behind

Look-ahead and look-behind assertions are not used in this regex pattern. These assertions allow checking for patterns ahead or behind the current match position without including them in the match itself.

## Author

Thanks for reading! Feel free to get in touch with me.  
[GitHub](https://github.com/JTruehitt)
