Word splitting is performed on the results of ==unquoted==:
	parameter expansions,
	command substitutions,
	arithmetic expansions

The characters used to split words are governed by the ==IFS== (Internal Field Separator) variable. It contains a space, tab and a new line.

It reveals empty result when we try to access:
```sh
echo ${IFS} # 
```

But using the special syntax, we can access it:
```sh
echo ${IFS@Q} # $' \t\n'
```

Because IFS doesn't have splitting via commas, even though the numbers is not quoted, it won't split the word from the commas
```sh
numbers=1,2,3,4,5
touch $numbers
ls

1,2,3,4,5
```

To achieve this, we need to modify the IFS:
```sh
IFS=","
touch $numbers

1 2 3 4 5 1,2,3,4,5 # 6 files
```
