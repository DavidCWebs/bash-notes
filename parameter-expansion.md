# Parameter Expansion

Substitution
------------
* `${VARIABLE%suffix}` Remove shortest matching suffix from VARIABLE
* `${VARIABLE%suffix*}` Remove characters from suffix to end from VARIABLE
* `${VARIABLE%%suffix}` Remove longest matching suffix from VARIABLE
* `${VARIABLE%%suffix*}` Remove chars from the suffix furthest from end from VARIABLE
* `${VARIABLEi#prefix}` Remove prefix from VARIABLE
* `${VARIABLE/old/new}` Replace first match of old with new
* `${VARIABLE//old/new}` Replace all instances of old with new
* `${VARIABLE/%old/new}` Replace old suffix with new
* `${VARIABLE/#old/new}` Replace old prefix with new

Slicing
-------
Uses the form `${VARIABLE:offset:length}`

If no offset is specified, the match goes to the end of the string.

Length is **exclusive** so if you want the first 3 characters of the string you should use `${VAR:0:3}` to get chars from index 0, 1, and 2.

```bash
VAR="hello world"
echo "${VAR:1}" # outputs "ello world"
echo "${VAR:0:5}" # outputs "hello"
```

### Remove Trailing Slash on Variable
```bash
#!/bin/bash
read -p "Enter path: " INPUT
INPUT=${INPUT%/}
```

### Remove File Extension
```bash
FILENAME=test.txt
FILENAME=${FILENAME%.*}
echo "${FILENAME}" # Outputs test
```

### Get File Extension
```bash
FILENAME=test.txt
echo "${FILENAME#*.}" # Remove all from start to '.'
EXT=${FILENAME#*.} # Assign to a new variable
```


References
----------
* [Shell parameter expansion][2]
* [Bash cheatsheet, devhints][1]
* [Linux Journal article on parameter expansion][3]

[1]: https://devhints.io/bash
[2]: https://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html
[3]: https://www.linuxjournal.com/content/bash-parameter-expansion