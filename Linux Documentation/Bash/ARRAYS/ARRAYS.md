
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