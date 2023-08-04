## Concepts
- regex is a tool/library to do advanced search over strings using patterns
- compatible with diff languages

## BackSlash \
- to escape special characters
```
$ \. // finds .
$ \\ // searches for a backslash
$ .* // skip everything after, even spaces
```

## Meta Characters (need to be escaped)
```
$ .[{()\^$|?*+
$ . // Match any character except new line
$ \d // Digit 0-9
$ \D // Not a Digit 0-9
$ \w // word character (a-z, A-Z, 0-9, _)
$ \W // Not a word character
$ \s // Whitespace (space, tab, newline)
$ \S // Not Whitespace (space, tab, newline)
$ [] // character set to match a specific character
$ () // groups to match group of characters
```

## Anchors
- match invisible positions before or after characters
```
$ \b // Word Boundary like \bHa\b
$ \B // Not a Word Boundary
$ ^ // Beginning of a String
$ $ // End of a String
```

## Quantifiers
```
$ * // 0 or More
$ + // 1 or More
$ ? // 0 or One very useful when you want to say if a character or group is optional
$ {3} // Exact Number
$ {3,4} // Range of Numbers (Minimum, Maximum)
```

## Practical Examples
```
$ [-.] // looks for "-" or "." once
$ [89]00 // find 800 or 900 numbers
$ [1-7] // match any number between 1 and 7
$ [a-z] // match any character between a and z
$ [a-zA-Z] // look for any character
$ [^a-z] // match anything that is not a-z
$ [^b]at // match everything except bat that ends with "at"
$ \d{3}.\d{3}.\d{4} // match 3 digits size 
$ Mr\.?\s[A-Z]\w* \\ * used to grap all words cz we don't know how much characters
$ M(r|s|rs) // match and r or an s 
$ [a-zA-Z0-9.-]+@[a-zA-Z-]+\.(com|edu|net) // match emails
$ [a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9.]+ // match any email
$ https?://(www\.)?\w+\.\w+ // match websites .. https?  means its optional
```

## Back References
- some use "%"
- back references are used to reference our captured groups
- examples: https://www.google.com or https://youtube.com
```
$ https?://(www\.)?\w+\.\w+
```
- replace tab:  Group 0 // implicit group which is all our url matches
- replace tab: Group 1: $1 // grabs first group of www, $1 is reference to our first group
- replace tab: Group 2: $2 // grabs second group of domain names
- replace tab: Group 3: $3 // grabs third group of top level domain names
```
$ $2$3 // filter/clean urls from http and other stuff and only include google.com or youtube.com or nasa.gov
```
