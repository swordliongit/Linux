### Notes:
1. PATH variable tells shell to look for executables
2. By modifying and including our script directory in the PATH variable, we can our scripts from anywhere in the system


1. If we have a script in this directory : ~/bash_exp/scripts/backup.sh
2. Go into home directory and edit the .profile file:
```sh
vim ~/.profile
```
3. Add the export command to the bottom of the script:
```sh
export PATH="$PATH:$HOME/bash_exp/scripts"
```
4. Reload the .profile file:
```sh
source ~/.profile
```
5. Now we can the backup.sh script in anywhere:
```sh
swordwsl@SWORD:~$ backup.sh
Hello World
```