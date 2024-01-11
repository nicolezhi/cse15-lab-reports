# **Week 1 Lab Report**

## cd examples

example of cd with no arguments
```
# [user@sahara ~]$ cd 
```

cd with path to a directory as an argument
```
# [user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$
```
cd with path to a file as argument
```
# [user@sahara ~]$ cd messages
[user@sahara ~/lecture1/messages]$
```
***

## ls examples

ls with no arguments
```
# [user@sahara ~]$ ls
lab1  lecture1
```

ls with path to a directory as an argument
```
# [user@sahara ~]$ ls lecture1
Hello.class  Hello.java  messages  README
```

ls with path to file as an argument
```
# [user@sahara ~]$ ls Hello.class
ls: cannot access 'Hello.java': No such file or directory
```
There is an error because there are no files within the Hello.java file.

***

## cat examples

cat with no arguments
```
# [user@sahara ~]$ cat

```

cat with path to a directory as an argument
```
# [user@sahara ~]$ cat lecture1
cat: lecture1: Is a directory
```
cat with path to a file as an argument
```
# [user@sahara ~]$ cat en-us.txt
cat: en-us.txt: No such file or directory
```
