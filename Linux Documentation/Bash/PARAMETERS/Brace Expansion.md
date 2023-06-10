
```sh
echo {1,2,3,4,5,6} # 1 2 3 4 5 6
```

```sh
echo {1..6} # 1 2 3 4 5 6
```

## Creating Multiple Files

Creating 12 folders named month01, month02, ..., month12
```sh
mkdir month{01..12}
```

Then creating 31 txt files inside each of those folders named day01, day02, ..., day31
```sh
touch month{01..12}/day{01..31}.txt
```

## Step Size

```sh
echo {1..10..2} # 1 3 5 7 9
```