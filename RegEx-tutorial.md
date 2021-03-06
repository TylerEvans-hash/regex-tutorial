# Introduction to Regex ( Regular Expressions )

Regular expressions play a vital role in programming. They used very often in the following examples, search engines, syntax highlighting systems, and data validation. 

## Summary

Regular Expressions allow you to parse through a string (literal) and search for specific patterns. This will allow you to validate emails, passwords, etc.

Here are a few examples regular expressions used to validate an email:

    1. (?:[a-z0-9!#$%&'*+/=?^_`{|}~-]+(?:\.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)*|"(?:[\x01-\x08\x0b\x0c\x0e-\x1f\x21\x23-\x5b\x5d-\x7f]|\\[\x01-\x09\x0b\x0c\x0e-\x7f])*")@(?:(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?\.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?|\[(?:(?:(2(5[0-5]|[0-4][0-9])|1[0-9][0-9]|[1-9]?[0-9]))\.){3}(?:(2(5[0-5]|[0-4][0-9])|1[0-9][0-9]|[1-9]?[0-9])|[a-z0-9-]*[a-z0-9]:(?:[\x01-\x08\x0b\x0c\x0e-\x1f\x21-\x5a\x53-\x7f]|\\[\x01-\x09\x0b\x0c\x0e-\x7f])+)\])

    2. /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

These specific regex were written to validate emails. There are definitely many other ways to do this, but this is just an example.

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

        This would output true in the console. The regex used in this exampls is /^R/. This uses the caret anchor to specify the begining of the string and the 'R' is the letter that we want to test. Since 'R' is the first letter in the string 'Regex', the text returns true.

    Dollar Anchor example:
        Let's say we have the string 'Regex' and we want to check that it ends with the letter 'x'.

            let string = 'Regex';
            console.log(/x$/.test(string));

        The console would logout true, as in this case the '$' signifies the end of the string. Notice that the anchor comes after the letter that you want to verify, unlike the caret which comes before to signify the beginning. 

### Quantifiers

Quantifiers allow you to match the number of instances of a specified character, group, or character class within a given string.

    Quantifier Example:
        Let's say you wanted to find the year from a date within a string. You can use quantifiers to do this.

            let string = 'The date is 7/29/2020';
            let regex = /\d{4}/;

            let result = string.match(regex);

            console.log(result);

        Console would display an array of ["2020"]. This regex is looking for 4 digits in a sequence and is the same as /\d\d\d\d/. Although this would leave out the month and the day, this regex would only work if the year was not abreviated.

### OR Operator

The OR operator | allows you to find alternations in a string.

    OR Operator examples:
        Let's say you want to choose between multiple characters in the spelling of the word grey/gray.

            let string = 'There are two spellings of grey and gray';
            let regex = /gr(e|a)y/g;

            let result = string.match(regex);

            console.log(result);

        The output would show both 'grey' and 'gray'. Take a look at the regex used in this example. The OR operator is used inbtween the two different characters that are allowed '(e|a)'. So the string can contain an 'e' or an 'a' in grey/gray.

        Let's say you want to find the words 'spaghetti' or 'bread' in a string.

            let string = 'I like both spaghetti and garlic bread together';
            let regex = /spaghetti|bread/gi;

            let result = string.match(regex);

            console.log(result);

        The output would be an array of ['spaghetti', 'bread']. This examples regex looks for 'spaghetti' or 'bread' and returns them to the result variable in an array.

### Character Classes

Character classes in regex refers to characters or symbols that belong to a certain set. Such as the 'word' class, this is any wordly character that is a letter of the Latin alphabet.

    Here are a few classes:
        1. \w - Word class (a-z, A-Z)
        2. \d - Digit class (0-9)
        3. \s - Space class (refers to spaces in a string)

    Example: 
        Let's say you wanted to change the formatting of a formatted phone number to one string with just numbers and no spaces. To do this we will be using the 'g' flag which will look for all of the specified search and the join() method as well.

            let string = '+1(234)567-8901'
            let regex = /\d/g;

            let result = string.match(regex).join('');

            console.log(result);

        The output would be ['12345678901'].
        Without the join method the output would be ['1', '2', '3', '4', '5', '6', '7', '8', '9', '0', '1'].

        This is a simple way to get all of a specific character class in one string.

### Flags

When writing Regular Expression flags may be used to affect the search. Listed below are the 6 flags that are in JavaScript along with a brief explanation.

1. i - This flag changes the search to be case-insensitive, so that there is no difference between A and a. This is important if you are looking for a specific word that can be capitalized or lowercased given the circumstances.

2. g - This flag allows the search to look for all matches. If this flag is not used, the search will only return the first match.

3. m - This is changes the search into 'Multiline' mode. This means if there is a string that has multiple lines, such as a paragraph, the search will be through each line.

4. s - This flag  changes  the search into 'dotall' mode. This allows a dot '.' to match the newline character \n

5. u - This flag enables full Unicode support in the search. This means that if you were to search emojis or special characters such as A ??? ???, then you can you \p{L} to find a letter in an language.

6. y - This is the 'sticky' flag. This allows the search to be performed at a given position in the string. An example of this would be syntax highlighting systems. When you declare a variable in JavaScript, let var = 'string'; the Syntax system looks at position 4 since it needs to read the variable name.

### Grouping and Capturing

Grouping is an essential part of writing regular expressions and is denoted using parenthesis (). Inside the paranthesis is what you are grouping together, whether that be letters or digits. With grouping you can validate data and formatting, find emails or specific words in a string such as domains.

    Example:
        Let's say you wanted to find emails in a string.

            let string = 'This is the email test@test.com and the rest is just irrelevant';
            let regex = /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/;

            let result = string.match(regex);

            console.log(result);

        The output: ['test@test.com']

        Let's break the regex down.

            The first grouping, ([a-z0-9_\.-]+), is searching for a string consisting of letters or numbers followed by dots underscores or hyphens
            After the first grouping there is an @ symbol
            The Second grouping, ([\da-z\.-]+), is searching for a 'digit' class or letters a-z followed by dots underscores or hyphens
            After the second grouping there is a '.'
            The Third grouping, ([a-z\.]{2,6}), is searching for a string of letters followed by dots underscores or hyphens

### Bracket Expressions

Brackets are used to indicate a set of specific characters to match, so any characters between the brackets will match. 

    Example: 
        Let's say you were given the string 'pandamonium' and your task was to find all the 'a' and 'o' charactes in it. The following code shows how to do that.

            let string = 'pandamonium';
            let regex = /[ao]/g;

            let result = string.match(regex);

            console.log(result);

        The output would be ['a', 'a, 'o']

Curly braces are used to specify an exact amount of times a thing is to match. Curly braces come after an expression. See below for an example.

    Example:
        Let's say you were given 'banana' and you needs to find 'nana'

            let string = 'banana';
            let regex = /na{2}/;

            let result = string.match(regex);

            console.log(result);

        The output would be matched to ['nana']. In this instance na occurs twice

### Greedy and Lazy Match

Greedy, denoted by using '.+',  means that the match will be the longest possible string. And Lazy, denoted by using '.+?',  means the match will be the shortest possible string.

    Greedy Example:

        let string = 'supercalifragilisticexpialidocious';
        let regex = /s.+i/;

        let result = string.match(regex);

        console.log(result); // supercalifragilisticexpialidoci

    Lazy Example:

        let string = 'supercalifragilisticexpialidocious';
        let regex = /s.+?i/;

        let result = string.match(regex);

        console.log(result); // supercali

### Boundaries

Boundaries allows the search to look for a specific string and only that string. Denoted with \b at the beginning of and/or end of a string.

    Example:

        let string = 'I love coding!! I also like to play music';
        let regex = /\bcoding\b/;

        let result = string.match(regex);

        console.log(result); // true

### Back-references

Back References are used when there is a group. Denoted by \N, where N is the group number, or by \k<name>, where name is a reference to a named group.

    \N Example: 

        let string = `The boy said: "That's not fair!!!".`;
        let regex = /(['"])(.*?)\1/g;

        let result = string.match(regex);
        
        console.log(result); // "That's not fair!!!"

    In this example the \1 in the regex refers to the grouping (['"]). Since the single ' is in the first index of the grouping the \1 refers back to this.

    \k<name> Example:

        let string = `The boy said: "That's not fair!!!".`;
        let regex = /(?<quote>['"])(.*?)\k<quote>/g;

        let result = string.match(regex);

        console.log(result); // "That's not fair!!!"

    In this example the " is first in the string to occur. This is then saved in the \k<name>. Once the \k<quote> is referenced it chooses the "

### Look-ahead and Look-behind

Look-ahead is used when you want to find something but only when it is immediately followed by something else. Denoted by X(?=Y) where X is what it looks for and Y is what follows it immediately.

    Example: 

        let string = 'I have 2 sodas, but I they were about 5??? each';
        let regex = /\d+(?=???)/;

        let result = string.match(regex);

        console.log(result); // 5

    In this case the grouping of (?=???) is the specified Y in the explanation above.

Look-behind is used when you want to find something but only when it comes after something. Denoted by (?<=Y)X where X is what it looks for and Y is what comes first.

    Example: 

        let string = 'I have 2 sodas, but I they were about $5 each';
        let regex = /(?<=\$)\d+/;

        let result = string.match(regex);

        console.log(result); // 5

    In this case the grouping of (?<=\$) is the specified Y in the explanation above.

## Author

Hello my name is Tyler! This is a project I made to help out beginners to Regular Expressions. I hope this gives you a simple understanding of what regular exressions are and how they are used.

### Authors Git-Hub
- https://github.com/TylerEvans-hash/