
## Accessing all the elements
```sh
$ echo ${array[@]}
```

## Indexing

Uses the same formula ==${parameter:offset:length}==

```sh
$ numbers=(1 2 3 4)
$ echo ${numbers[@]:1:2}

2 3
```

## Adding New Elements

```sh
$ numbers+=(5)
$ echo ${numbers[@]}

1 2 3 4 5
```

## Removing Elements
```sh
$ unset numbers[2]
$ $ echo ${numbers[@]}

1 2 4
```

When you remove an element, it's index also is removed. Bash won't auto adjust the index numbers:
```sh
$ echo ${!numbers[@]}

0 1 3 
```

## Changing Elements
```sh
numbers[1]=b
```

## Converting into Arrays - Readarray
[[Converting into Arrays - Readarray]]
Let's say that we have a txt file with the following content:
```sh
Monday
Tuesday
Wednesday
Thursday
Friday
Saturday
Sunday
```

We can direct the content as an input to the readarray command and it will create an array out of the file:
```sh
$ readarray dayarray < days.txt
$ echo ${dayarray[@]}

Monday Tuesday Wednesday Thursday Friday Saturday Sunday
```

### Sneaky Extra Characters

if we check with the special syntax we can see that the array elements actually have extra characters:
```sh
$ echo ${dayarray[@]@Q}

$'Monday\n' $'Tuesday\n' $'Wednesday\n' $'Thursday\n' $'Friday\n' $'Saturday\n' $'Sunday\n'
```

We can remove these special characters using the ==-t== argument:
```sh
$ readarray dayarray < days.txt
$ echo ${dayarray[@]@Q}

'Monday' 'Tuesday' 'Wednesday' 'Thursday' 'Friday' 'Saturday' 'Sunday'
```

## Converting Command Outputs into Arrays:
```sh
$ readarray -t files < <(ls ~/bash_exp/scripts/readarray)
```

## For Loops and Iterating Over Arrays
[[For Loops and Iterating Over Arrays]]
```sh
for variable in var1 var2 var3 ...; do
	...
done
```

```sh
for element in "${array[@]}"; do
	...
done
```

![[Arrays+and+For+Loops+Cheatsheet.pdf]]