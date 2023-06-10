
## &
Runs the command behind it in background. It runs them asynchronously
```sh
echo "hello" & echo "world"
```

## ;
Separates commands and it doesn't care if the previous command was successful or not
```sh
$ cd /unknown-dir ; echo "hello"

-bash: cd: /unknown-dir: No such file or directory
hello
```

## &&
Runs the second command only if the first command was successful
```sh
$ echo 123 && echo 456

123
456
```

## ||
Runs the second command only if the first one wasn't successful
```sh
$ echo 123 || echo 456

123
```

```sh
$ ls random_dir || echo 123
ls: cannot access 'random_dir': No such file or directory
123
```

## Ternary
```sh
commandA && commandB || commandC
```