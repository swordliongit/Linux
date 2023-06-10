```sh
tar [OPTION...] [FILE]...
```

## Example:

Creating a tar archive out of all the files in the folder and placing it 1 directory above:
```sh
tar -cvf ../my_backup_"$(date +%d-%m-%Y_%H-%M-%S)".tar ./* 2>/dev/null
```
