1. Tokenization
2. Command Identification
3. Expansion
4. Word Splitting
5. Globbing


## Word Splitting
[[Word Splitting]]

Word splitting is performed on the results of ==unquoted==:
	parameter expansions,
	command substitutions,
	arithmetic expansions

The characters used to split words are governed by the ==IFS== (Internal Field Separator) variable. It contains a space, tab and a new line.

It reveals empty result when we try to access:
```sh
echo ${IFS} # 
```

But using the special syntax, we can access it:
```sh
echo ${IFS@Q} # $' \t\n'
```

## Globbing - Pattern Matching
[[Globbing - Pattern Matching]]

Upon reaching the globbing stage, bash scans each word for unquoted special pattern characters. These special pattern characters are \*, ?, \[

## *
*Matches any string, regardless of length or content. Also matches empty strings.*

## ?
*Matches any single character but requires a character in its place*
```sh
swordwsl@SWORD:~/bash_exp/scripts/month01$ ls
day01.txt  day04.txt  day07.txt  day10.txt  day13.txt  day16.txt  day19.txt  day22.txt  day25.txt  day28.txt  day31.txt
day02.txt  day05.txt  day08.txt  day11.txt  day14.txt  day17.txt  day20.txt  day23.txt  day26.txt  day29.txt
day03.txt  day06.txt  day09.txt  day12.txt  day15.txt  day18.txt  day21.txt  day24.txt  day27.txt  day30.txt
swordwsl@SWORD:~/bash_exp/scripts/month01$ ls day0?.txt
day01.txt  day02.txt  day03.txt  day04.txt  day05.txt  day06.txt  day07.txt  day08.txt  day09.txt
```

## \[
*Matches any one of the enclosed characters, but requires a character to be there.*
```sh
swordwsl@SWORD:~/bash_exp/scripts/month01$ ls
day01.txt  day04.txt  day07.txt  day10.txt  day13.txt  day16.txt  day19.txt  day22.txt  day25.txt  day28.txt  day31.txt
day02.txt  day05.txt  day08.txt  day11.txt  day14.txt  day17.txt  day20.txt  day23.txt  day26.txt  day29.txt
day03.txt  day06.txt  day09.txt  day12.txt  day15.txt  day18.txt  day21.txt  day24.txt  day27.txt  day30.txt
swordwsl@SWORD:~/bash_exp/scripts/month01$ ls day[01]2.txt
day02.txt  day12.txt
```

### Ranged Matching
```sh
swordwsl@SWORD:~/bash_exp/scripts/folder01$ ls
file001.txt  file010.txt  file019.txt  file028.txt  file037.txt  file046.txt  file055.txt  file064.txt  file073.txt  file082.txt  file091.txt  file100.txt
file002.txt  file011.txt  file020.txt  file029.txt  file038.txt  file047.txt  file056.txt  file065.txt  file074.txt  file083.txt  file092.txt
file003.txt  file012.txt  file021.txt  file030.txt  file039.txt  file048.txt  file057.txt  file066.txt  file075.txt  file084.txt  file093.txt
file004.txt  file013.txt  file022.txt  file031.txt  file040.txt  file049.txt  file058.txt  file067.txt  file076.txt  file085.txt  file094.txt
file005.txt  file014.txt  file023.txt  file032.txt  file041.txt  file050.txt  file059.txt  file068.txt  file077.txt  file086.txt  file095.txt
file006.txt  file015.txt  file024.txt  file033.txt  file042.txt  file051.txt  file060.txt  file069.txt  file078.txt  file087.txt  file096.txt
file007.txt  file016.txt  file025.txt  file034.txt  file043.txt  file052.txt  file061.txt  file070.txt  file079.txt  file088.txt  file097.txt
file008.txt  file017.txt  file026.txt  file035.txt  file044.txt  file053.txt  file062.txt  file071.txt  file080.txt  file089.txt  file098.txt
file009.txt  file018.txt  file027.txt  file036.txt  file045.txt  file054.txt  file063.txt  file072.txt  file081.txt  file090.txt  file099.txt
swordwsl@SWORD:~/bash_exp/scripts/folder01$ ls file0[2-5]?.txt
file020.txt  file024.txt  file028.txt  file032.txt  file036.txt  file040.txt  file044.txt  file048.txt  file052.txt  file056.txt
file021.txt  file025.txt  file029.txt  file033.txt  file037.txt  file041.txt  file045.txt  file049.txt  file053.txt  file057.txt
file022.txt  file026.txt  file030.txt  file034.txt  file038.txt  file042.txt  file046.txt  file050.txt  file054.txt  file058.txt
file023.txt  file027.txt  file031.txt  file035.txt  file039.txt  file043.txt  file047.txt  file051.txt  file055.txt  file059.txt
```

## \[!
*Matches any single character except those enclosed in the brackets, but requires a character to be there.*
```sh
swordwsl@SWORD:~/bash_exp/scripts/month01$ ls
day01.txt  day04.txt  day07.txt  day10.txt  day13.txt  day16.txt  day19.txt  day22.txt  day25.txt  day28.txt  day31.txt
day02.txt  day05.txt  day08.txt  day11.txt  day14.txt  day17.txt  day20.txt  day23.txt  day26.txt  day29.txt
day03.txt  day06.txt  day09.txt  day12.txt  day15.txt  day18.txt  day21.txt  day24.txt  day27.txt  day30.txt
swordwsl@SWORD:~/bash_exp/scripts/month01$ ls day[!0]*.txt
day10.txt  day12.txt  day14.txt  day16.txt  day18.txt  day20.txt  day22.txt  day24.txt  day26.txt  day28.txt  day30.txt
day11.txt  day13.txt  day15.txt  day17.txt  day19.txt  day21.txt  day23.txt  day25.txt  day27.txt  day29.txt  day31.txt
```

---

## Combined Example:
```sh
swordwsl@SWORD:~/bash_exp/scripts/folder01$ ls
file001.txt  file010.txt  file019.txt  file028.txt  file037.txt  file046.txt  file055.txt  file064.txt  file073.txt  file082.txt  file091.txt  file100.txt
file002.txt  file011.txt  file020.txt  file029.txt  file038.txt  file047.txt  file056.txt  file065.txt  file074.txt  file083.txt  file092.txt
file003.txt  file012.txt  file021.txt  file030.txt  file039.txt  file048.txt  file057.txt  file066.txt  file075.txt  file084.txt  file093.txt
file004.txt  file013.txt  file022.txt  file031.txt  file040.txt  file049.txt  file058.txt  file067.txt  file076.txt  file085.txt  file094.txt
file005.txt  file014.txt  file023.txt  file032.txt  file041.txt  file050.txt  file059.txt  file068.txt  file077.txt  file086.txt  file095.txt
file006.txt  file015.txt  file024.txt  file033.txt  file042.txt  file051.txt  file060.txt  file069.txt  file078.txt  file087.txt  file096.txt
file007.txt  file016.txt  file025.txt  file034.txt  file043.txt  file052.txt  file061.txt  file070.txt  file079.txt  file088.txt  file097.txt
file008.txt  file017.txt  file026.txt  file035.txt  file044.txt  file053.txt  file062.txt  file071.txt  file080.txt  file089.txt  file098.txt
file009.txt  file018.txt  file027.txt  file036.txt  file045.txt  file054.txt  file063.txt  file072.txt  file081.txt  file090.txt  file099.txt
swordwsl@SWORD:~/bash_exp/scripts/folder01$ ls file0[2][!2].txt
file020.txt  file021.txt  file023.txt  file024.txt  file025.txt  file026.txt  file027.txt  file028.txt  file029.txt
```

---

## Redirection
[[Redirection]]
## Data Streams

Stream 0 = Standard Input(stdin)
Stream 1 = Standard Output(stdout)
Stream 2 = Standard Error(stderr)

### Dumping the content into a file and retrieving it back:
```sh
$: echo "hello world" > hello.txt
$: cat < hello.txt
hello world
```

## Standard Output and Standard Error( 2> &>)
\>

#### Redirecting Errors

Trying to cd into root gives us an error:
```sh
swordwsl@SWORD:~/bash_exp/scripts$ cd /root
-bash: cd: /root: Permission denied
```

If we try to redirect the output to a txt file, we still get the error printed on the terminal:
```sh
swordwsl@SWORD:~/bash_exp/scripts$ cd /root > error.txt
-bash: cd: /root: Permission denied
```

To avoid this, we have to use the standard error redirection ==2>==:
```sh
swordwsl@SWORD:~/bash_exp/scripts$ cd /root 2> error.txt
```

```sh
swordwsl@SWORD:~/bash_exp/scripts$ cat error.txt
-bash: cd: /root: Permission denied
```

Note that we can't use the error redirection to redirect standard output:
```sh
swordwsl@SWORD:~/bash_exp/scripts$ echo "hello world" 2> hello.txt
hello world
```

#### Redirecting Errors and Output

To redirect both the errors and the output we have to use the ==&>==:
```sh
swordwsl@SWORD:~/bash_exp/scripts$ cd /root &> error.txt
```

---

### Scraping Output
==/dev/null==
```sh
swordwsl@SWORD:~/bash_exp/scripts$ cd /root &> /dev/null
```

---

## Appending to the Output
If we use the double direction operator, the output won't overwrite the file but append to it.
==\>>==
==\2>>==
==&>>==
```sh
swordwsl@SWORD:~/bash_exp/scripts$ cat error.txt
-bash: cd: /root: Permission denied

swordwsl@SWORD:~/bash_exp/scripts$ cd /root 2>> error.txt
swordwsl@SWORD:~/bash_exp/scripts$ cd /root 2>> error.txt

swordwsl@SWORD:~/bash_exp/scripts$ cat error.txt
-bash: cd: /root: Permission denied
-bash: cd: /root: Permission denied
-bash: cd: /root: Permission denied
```

---

![[Command-Line-Processing-Cheatsheet 1.pdf]]