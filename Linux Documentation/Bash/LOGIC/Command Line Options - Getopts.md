**Notes:**

1. getopts processes the next command option each loop, puts active option in the defined "option" variable and puts the value of that option in the ==$OPTARG== variable
2. getopts puts the unaccepted options into the ==?== variable. We can use it to check for default cases.

```sh
while getopts "f:c:" opt; do
    case "$opt" in
        c)
            result=$(echo "scale=2; ($OPTARG * (9/5)) + 32" | bc)
            ;;
        f)
            result=$(echo "scale=2; ($OPTARG - 32) * (5/9)" | bc)
            ;;
        \?);;
    esac
done
```

### Timer Example
*timer.sh*
```sh
#!/bin/bash

total_seconds=""

while getopts "m:s:" opt; do
    case "$opt" in
        m) 
        total_seconds=$(($total_seconds + $OPTARG * 60))
        ;;
        s) 
        total_seconds=$(($total_seconds + $OPTARG))
        ;;
    esac
done

while [ "$total_seconds" -gt 0 ]; do
    echo "$total_seconds"
    total_seconds=$(($total_seconds - 1))
    sleep 1s
done

echo "Time's up!"

exit 0
```

```sh
$ timer.sh -m 1 -s 5
```
It will start counting from 65 seconds because of our 1 min and 5 second options.