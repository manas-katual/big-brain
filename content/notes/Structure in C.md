---
title: Structure in C
draft: false
tags:
---
Uplink : [[C]]

Structure is user defined data types just like int, float, char is a data type which pre-defined structure is something a user defines 

example
```c
struct student
{
    int roll;
    int marks;
    float per;
    char name[10];
};

void main()
{
    struct student s1;
    printf("Enter your roll, marks, percentage, name: ");
    scanf("%d %d %f %s",&s1.roll,&s1.marks,&s1.per,s1.name);
    printf("%d %d %.2f %s",s1.roll,s1.marks,s1.per,s1.name);
    getch();
}

```
here `%.2f` means it will print only upto 2 decimals like it round off the number and while using `%s` which defines [[String in C|String]] we don't put `&`