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

## Sneaky Extra Characters
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

