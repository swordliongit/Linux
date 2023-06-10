**Notes:**
1. Test commands return 0 if true and 1 if false
2. $? variable returns the exit code of the test command
3. They compare only integers


## \[ ] vs \[\[ ]]

Inside the single square brackets, word splitting still occurs so you have to quote the variables to get the correct result. Whereas in double brackets, word splitting doesn't occur.

---

```sh
$ [ 2 -eq 2 ]; echo $?

0
```

## Conditional Operators
1. ==-eq==
2. ==-ne==
3. ==-gt==
4. ==-lt==
5. ==-geq==
6. ==-leq==

## String Test Operators
1. ==\===
2. ==!\===
3. Checking if string empty: -z
```sh
$ [[ -z $str ]];
```
4. Checking if string is not empty: -n
```sh
$ [[ -n $str ]]
```


```sh
$ a="hello"
$ b="goodbye"
$ [ $a = $b ]; echo $?

1
```

## File Test Operators
1. Checking if file exists: ==-e==
2. Checking file is a normal file: ==-f==
3. Checking if something is directory: ==-d==
4. Checking if file exists and have execution permissions: ==-x==