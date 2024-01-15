# **Week 1 Lab Report**

## cd examples

example of cd with no arguments
```
# [user@sahara ~]$ cd
[user@sahara ~]$
```
The program changes directory back to the default (home) since there is no argument.

cd with path to a directory as an argument
```
# [user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$
```
The program changes directory to the lecture1 directory.

cd with path to a file as argument
```
# [user@sahara ~]$ cd messages
[user@sahara ~/lecture1/messages]$
```
The program changes directory to the messages directory, inside lecture1.

***

## ls examples

ls with no arguments
```
# [user@sahara ~]$ ls
lab1  lecture1
```
The output lists the directories in the workspace, which are lab1 and lecture1.

ls with path to a directory as an argument
```
# [user@sahara ~]$ ls lecture1
Hello.class  Hello.java  messages  README
```
The output lists the files within the lecture1 directory.

ls with path to file as an argument
input: /home/lecture1/messages
```
# [user@sahara ~]$ ls en-us.txt
en-us.txt
```
The output repeats the file name given in the argument.

***

## cat examples

cat with no arguments
```
# [user@sahara ~]$ cat

```

cat with path to a directory as an argument
input: /home
```
# [user@sahara ~]$ cat lecture1
cat: lecture1: Is a directory
```
cat with path to a file as an argument
input: /home/lecture1/messages
```
# [user@sahara ~]$ cat en-us.txt
Hello World!
```
