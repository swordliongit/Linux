Command line arguments are passed to the positional parameters in the scripts

script:
```sh
echo "First param: $1"
echo "Second param: $2"
```

```sh
script.sh param1 param2
			$1     $2
```