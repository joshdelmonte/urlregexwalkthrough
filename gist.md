# URL Regex Walkthrough

~The following information is essentially a brief cliffnote and explanation of a URL regex(regular expression).    

## Summary

~URL's are many, and we want matches that will meet the perameters set by this array of code:

    -`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

~Our URLs can be dissected into five different parts in this order:
    -the protocol (`https://`)
    -the subdomain (`www` etc.)
    -the domain (i.e. facebook, google, github, etc.)
    -the domain extension (`.com`, `.org`, `.gov` etc.)
    -the path (usually following the domain extension with a slash and unique code specific to that endpoint)

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

~Regex components are literal, and the boiler plate for them for us to get started is we have to define them with opening and closing forward slashes (`/`), and the beginning and end defined by a carrot (`^`) and a dollar sign(`$`) at the end, BUT both are within these slashes. The rest is up to us to define in the anchors, qantifiers, qualifiers, grouping constructs, and all the coming material to follow.

### Anchors

~The dollar sign and carrot ar our anchors, and as we've stated, this is to dictate beginning and end. The code will without a doubt read from beginning to end, but it will interpret the data in that order for us to recieve randomized matches.

### Quantifiers

~Our quantifiers give us a designated time we want them to match
    -`?` will allow us to match the pattern 0 or 1 time. We'll be using this in the beginning (`/^(https?:\/\/)?`) so it will match this once or not at all, and again in the end (`([\/\w \.-]*)*\/?`).

    -'*' allots us a generous zero to infinitely more matches. At the end we use this to generate all the varieties of paths therein(`([\/\w \.-]*)*\/?`).

    -`+` demands that there be one match or more like the previous `*` quantifier. Employed in `([\da-z\.-]+)` to produce matches of the subdomain.

    -`{}` or curly brackets/braces will set our LIMITS with an exact number of times {x}, a minimal amount of times {x, }, or a minimum and maximum {x, y} which is exactly what we are doing with  {2, 6}.

### Grouping Constructs

~We use grouping constructs in our URL for each of the afore mentioned url parts(protocol, subdomain, etc.) but we are going to define them and what we want to happen with them within (`()`) which we call a subexpression.

    -protocol : (`/^(https?:\/\/)?`)

    -subdomain & domain: (`([\da-z\.-]+)\.`)
    
    -domain extension: (`\.([a-z\.]{2,6})`)
    
    -path : (`([\/\w \.-]*)*`)


### Bracket Expressions

~Our bracket expressions within these brackets (`[]`) where we will put the characters we want to match in.
    
    -`([\da-z\.-]+)\.` allows us to access an array of digits (`\d`) with all letters a-z (`a-z`) to match one or more times `+` and separated from our other grouping constructs by a period `\.`

    -`([a-z\.]{2,6})` alots us an array of letters that can be anywhere from 2 to six characters in length to declare the domain matches.

    -`([\/\w \.-]*)` declares the subdomain path to mach zero or more times.

### Character Classes

~ Character classes will define a set of characters to fulfill a match, and this can include bracket expressions but this allows us to address other parameters we'd like to meet.

    - `\d` Any and all numbers within this expression will be met with matches unless specified. (`([\da-z\.-]+)`)

    -(`w`)   lets us match any and all characters, capital or otherwise, numbers, and even the humble underscore. essentially it 'simplifies' or translates from (`a-zA-Z,0-9_`) 

    -(`.`) will match all characters with the exception being the new line character. In the URL instance this will to separate our subdomain, domain, and domain extensions.

### The OR Operator

~In this regex we needn't a OR operator (`|`) but it allows to convert the expression they are grouped with to be output in an array independent of order and may arrange themselves in a variety of ways. 

--(`(dig):(bug)` would be interpreted as `(d|i|g):(b|u|g)` to randomize and interpret those letters in all ways possible like `idg:ubg` for example)

### Flags

~We haven't any flags but these are represented by (`g`) to tell the regex it should test for all of a strings potential matches as "Global Search", (`m`) urges regex for a "multi-line" search to generate multiple line matches, and (`i`) which is case insensitve searching which makes the case to be ignored to retrieve matching strings.

### Character Escapes

~Character escapes are always indicated by a backslash (`\`) which are used to interpret the data preceding them as literal. A sort of break 
    -Example: (`/^(https?:\/\/)?`)
    --Though it is like the outer backslashes, inside of them coupled with the apporpriate grouping construct, interprets the preceding slashes as literal while not interpreting themselves in the matches used only as indication.

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)

Thank you for reading the preceding body. May it help you with your understanding of a URL regex or any for that matter. Below I have a link to my github profile should you see fit.

        -Carpe Diem,
            Joshua Delmonte.