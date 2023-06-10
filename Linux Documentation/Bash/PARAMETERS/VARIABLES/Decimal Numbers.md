bc command lets us deal with decimal numbers, bc can be used directly:
```sh
bc
```

### Piping Results into bc
*This will give the output to the bc command and it will display the result*
```sh
echo "5/2" | bc
```

### Showing Decimal Numbers
==scale== variable determines the amount of digits after the dot
```sh
echo "scale=2; 5/2" | bc # 2.50
```