
```sh
${parameter:offset:length}
```

```sh
name="HelloWorld"

echo "${name:0:4}" # Hello
```

```sh
echo "${name:4}" # World 
```

```sh
echo "${name:4:}" # empty because nothing after : means zero
```

```sh
echo "${name: -3:3}" # orl
```

```sh
echo "${name: -3}" # orld
```