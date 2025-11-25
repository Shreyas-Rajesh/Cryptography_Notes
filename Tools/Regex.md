https://www.dataquest.io/cheat-sheet/regular-expressions-cheat-sheet/
A Regular Expression or RegEx is a special sequence of characters that uses a search pattern to find a string or set of strings. 

`\d` -  One unicode digit. 
`\w` - ASCII \ Unicodez letter, digit or underscore
`\s` - "whitespace character": any Unicode separator
`\D` - One character that is not a _digit_ as defined by your engine's _\d_

| Quantifier | Legend              | Example        |
| ---------- | ------------------- | -------------- |
| +          | One or more         | Version \w-\w+ |
| {3}        | Exactly three times | \D{3}          |
| {2,4}      | Two to four times   | \d{2,4}        |
| {3,}       | Three or more times | \w{3,}         |
| *          | Zero or more times  | A*B*C*         |
| ?          | Once or none        | plurals?       |

`|` - OR operator. matches either the expression to its left or its right, finding all possible matches across the string.
`[]` -  define a set, where each character is matched independently. A match occurs if any character from the set appears in the text.
`[ - ]` - The "-" is a range operator, matching any character from (left) to (right)
`[ ^ers ]` - negates these characters


Import the module - `re`
1. `match = search(string_to_search, "s")` - It searches the string "string_to_search" in the main string s. Creates a `match object`
	- `match object` contains: 
		1. The span (start and end indices) of the match.
		2. The exact substring that was matched (e.g., "portal").
		3. The original string searched.
	- `match.group()`: Returns the actual substring that was found
	- `match.start()`: Returns the starting index of the match.
	- `match.end()`: Returns the ending index of the match
	- `match.span()`: Returns a tuple containing the (start, end) indices of the match.
2. `match = re.findall()`: Returns all non-overlapping matches of a pattern in the string as a list. It scans the string from left to right.
3. `re.split(pattern, string, maxsplit=0, flags=0)`: 
	1. **flags (optional):** Apply regex flags like re.IGNORECASE.
	