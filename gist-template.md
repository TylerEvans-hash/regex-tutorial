# Introduction to Regex ( Regular Expressions )

Regular expressions play a vital role in programming. They used very often in the following examples, search engines, syntax highlighting systems, and data validation. 

## Summary

Regular Expressions allow you to parse through a string (literal) and search for specific patterns. This will allow you to validate emails, passwords, etc.

This is an example of a regular expression:
(?:[a-z0-9!#$%&'*+/=?^_`{|}~-]+(?:\.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)*|"(?:[\x01-\x08\x0b\x0c\x0e-\x1f\x21\x23-\x5b\x5d-\x7f]|\\[\x01-\x09\x0b\x0c\x0e-\x7f])*")@(?:(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?\.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?|\[(?:(?:(2(5[0-5]|[0-4][0-9])|1[0-9][0-9]|[1-9]?[0-9]))\.){3}(?:(2(5[0-5]|[0-4][0-9])|1[0-9][0-9]|[1-9]?[0-9])|[a-z0-9-]*[a-z0-9]:(?:[\x01-\x08\x0b\x0c\x0e-\x1f\x21-\x5a\x53-\x7f]|\\[\x01-\x09\x0b\x0c\x0e-\x7f])+)\])

This specific regex was written to validate emails. There are definitely many other ways to do this, but this is just an example.

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

Anchors are special characters that allow the you to mark the beginning of the text and the end of the text. 

    - ^ - The caret anchor marks the beginning of the text
    - $ - The dollar anchor marks the end of the text

    Caret Anchor example: 
        Let's say you wanted to check that the string 'Regex' starts with an 'R'. The following code will be an example of how you would use regular expressions to test this.

            let string = 'Regex';
            console.log(/^R/.test(string));

    This would output true in the console. The regex used in this exampls is /^R/. This uses the caret anchor to specify the begining of the string and the 'R' is the letter
    that we want to test. Since 'R' is the first letter in the string 'Regex', the text returns true.

    Dollar Anchor example:
        Let's say we have the string 'Regex' and we want to check that it ends with the letter 'x'.

            let string = 'Regex';
            console.log(/x$/.test(string));

    The console would logout true, as in this case the '$' signifies the end of the string. Notice that the anchor comes after the letter that you want to verify, unlike the caret which comes before to signify the beginning. 

### Quantifiers

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
