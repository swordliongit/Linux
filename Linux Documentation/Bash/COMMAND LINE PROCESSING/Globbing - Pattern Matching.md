
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
