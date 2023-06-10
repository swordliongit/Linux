Select is used to provide the user an option list to choose from. Runs infinitely by default.

An empty ==select== command will save the input to the ==$RESPONSE== variable

*select.sh:*
```sh
select option in CompEng Web Embedded Hardware Software Tester;
do
        echo "You have selected the option $option"
done
```

```sh
swordwsl@SWORD:~/bash_exp/scripts$ ./select.sh
1) CompEng
2) Web
3) Embedded
4) Hardware
5) Software
6) Tester
#?
```

## Breaking out of the do loop
```sh
select option in CompEng Web Embedded Hardware Software Tester;
do
        echo "You have selected the option $option"
        break
done
```

## Controlling Prompt of Select

==PS3== variable controls the prompt
```sh
PS3="Select your area of interest: "
select option in CompEng Web Embedded Hardware Software Tester;
do
        echo "You have selected the option $option"
        break
done
```

```sh
swordwsl@SWORD:~/bash_exp/scripts$ ./select.sh
1) CompEng
2) Web
3) Embedded
4) Hardware
5) Software
6) Tester
What is your area of interest?:
```