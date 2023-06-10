
read prompts the user an option to type in and it will store the result into the variables. Default variable is ==REPLY==

*script*
```sh
read inp1 inp2
echo $inp1 $inp2
```

```sh
$ ./script.sh
$ Sword Lion

Sword Lion
```

## Providing a Text Prompt

```sh
read -p "Enter your age: " age 
```

## Time Out
*prompt will disappear after specified time*
```sh
read -t 5 -p "Enter your age: " age
```

## Hiding Input
```sh
read -s -p "Enter your password: " passwd
```