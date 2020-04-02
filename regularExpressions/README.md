Source: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions

Creating a regular expression

let re = /ab+c/;

let re = new RegExp('ab+c');

Writing a regular expresion pattern

A regular expression pattern is composed of simple characters, such as /abc/, or a combination of simple and special characters, 
such as /ab*c/ or /Chapter (\d+)\.\d*/. The last example includes parentheses, which are used as a memory device.

Using simple patterns:
/abc/

Using special characters: 
We can add special character in regex
* means zero or more, + one or more

Assertions
Assertions include boundaries, which indicate the beginnings and endings of lines and words, and other patterns indicating in some way 
that a match is possible (including look-ahead, look-behind, and conditional expressions).

Example of Assertions

^	
Matches the beginning of input. If the multiline flag is set to true, also matches immediately after a line break character. 
For example, /^A/ does not match the "A" in "an A", but does match the first "A" in "An A".

This character has a different meaning when it appears at the start of a group.

$	
Matches the end of input. If the multiline flag is set to true, also matches immediately before a line break character. 
For example, /t$/ does not match the "t" in "eater", but does match it in "eat".

\b	
Matches a word boundary. This is the position where a word character is not followed or preceded by another word-character, such as between a letter and a space. Note that a matched word boundary is not included in the match. In other words, the length of a matched word boundary is zero.

Examples:

/\bm/ matches the "m" in "moon".
/oo\b/ does not match the "oo" in "moon", because "oo" is followed by "n" which is a word character.
/oon\b/ matches the "oon" in "moon", because "oon" is the end of the string, thus not followed by a word character.
/\w\b\w/ will never match anything, because a word character can never be followed by both a non-word and a word character.
To match a backspace character ([\b]), see Character Classes.

\B	
Matches a non-word boundary. This is a position where the previous and next character are of the same type: Either both must be words, 
or both must be non-words, for example between two letters or between two spaces. The beginning and end of a string are considered 
non-words. Same as the matched word boundary, the matched non-word boundary is also not included in the match. 
For example, /\Bon/ matches "on" in "at noon", and /ye\B/ matches "ye" in "possibly yesterday".

Character classes
Distinguish different types of characters. For example, distinguishing between letters and digits.

Examples of Character class

\d	Matches any digit (Arabic numeral). Equivalent to [0-9]. For example, /\d/ or /[0-9]/ matches "2" in "B2 is the suite number".

\D	Matches any character that is not a digit (Arabic numeral). Equivalent to [^0-9]. For example, /\D/ or /[^0-9]/ matches "B" in "B2 is the suite number".

\w	Matches any alphanumeric character from the basic Latin alphabet, including the underscore. Equivalent to [A-Za-z0-9_]. For example, /\w/ matches "a" in "apple", "5" in "$5.28", and "3" in "3D".

\W	Matches any character that is not a word character from the basic Latin alphabet. Equivalent to [^A-Za-z0-9_]. For example, /\W/ or /[^A-Za-z0-9_]/ matches "%" in "50%".


(?=y)	
Lookahead assertion: Matches "x" only if "x" is followed by "y". For example, /Jack(?=Sprat)/ matches "Jack" only if it is followed by "Sprat".
/Jack(?=Sprat|Frost)/ matches "Jack" only if it is followed by "Sprat" or "Frost". However, neither "Sprat" nor "Frost" is part of the match results.

x(?!y)	
Negative lookahead assertion: Matches "x" only if "x" is not followed by "y". For example, /\d+(?!\.)/ matches a number only if it is not followed by a decimal point. /\d+(?!\.)/.exec('3.141') matches "141" but not "3.

(?<=y)x	
Lookbehind assertion: Matches "x" only if "x" is preceded by "y". For example, /(?<=Jack)Sprat/ matches "Sprat" only if it is preceded by "Jack". /(?<=Jack|Tom)Sprat/ matches "Sprat" only if it is preceded by "Jack" or "Tom". However, neither "Jack" nor "Tom" is part of the match results.

(?<!y)x	
Negative lookbehind assertion: Matches "x" only if "x" is not preceded by "y". For example, /(?<!-)\d+/ matches a number only if it is not preceded by a minus sign. /(?<!-)\d+/.exec('3') matches "3". /(?<!-)\d+/.exec('-3')  match is not found because the number is preceded by the minus sign.

Groups and ranges
Indicate groups and ranges of expression characters.
x|y	
Matches either "x" or "y". For example, /green|red/ matches "green" in "green apple" and "red" in "red apple".

[xyz]
[a-c]	
A character set. Matches any one of the enclosed characters. You can specify a range of characters by using a hyphen, but if the hyphen appears as the first or last character enclosed in the square brackets it is taken as a literal hyphen to be included in the character set as a normal character. It is also possible to include a character class in a character set.

For example, [abcd] is the same as [a-d]. They match the "b" in "brisket", and the "c" in "chop".

For example, [abcd-] and [-abcd] match the "b" in "brisket", the "c" in "chop", and the "-" (hyphen) in "non-profit".

For example, [\w-] is the same as [A-Za-z0-9_-]. They both match the "b" in "brisket", the "c" in "chop", and the "n" in "non-profit".

[^xyz]
[^a-c]

A negated or complemented character set. That is, it matches anything that is not enclosed in the brackets. You can specify a range of characters by using a hyphen, but if the hyphen appears as the first or last character enclosed in the square brackets it is taken as a literal hyphen to be included in the character set as a normal character. For example, [^abc] is the same as [^a-c]. They initially match "o" in "bacon" and "h" in "chop".

Quantifiers
Indicate numbers of characters or expressions to match.

Unicode property escapes
Distinguish based on unicode character properties, for example, upper- and lower-case letters, math symbols, and punctuation.


