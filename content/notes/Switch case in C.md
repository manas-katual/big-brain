---
title: Switch case in C
draft: false
tags:
---
Uplink : [[C]]

Switch case is used for making menu driven programs for example we will write multiple lines in a single program like addition, Multiplication, subtraction, etc. But any one program will run according to the user.

example code :
```c
#include <stdio.h>
#include <conio.h>

void main()
{
    int ch, x, y, z;
    printf("Press 1, Addtion\n");
    printf("Press 2, Subtraction\n");
    printf("Press 3, Multiplication\n");
    printf("Enter your Choice: ");
    scanf("%d", &ch);
    switch (ch)
    {
	    case 1:
	    {
	        printf("Enter 2 numbers: ");
	        scanf("%d %d", &x, &y);
	        z = x + y;
	        printf("Addition is %d", z);
	    }
	    case 2:
	    {
	        printf("Enter 2 numbers: ");
	        scanf("%d %d", &x, &y);
	        z = x - y;
	        printf("Subtraction is is %d", z);
	        break;
	    }
	    case 3:
	    {
	        printf("Enter 2 numbers: ");
	        scanf("%d %d", &x, &y);
	        z = x * y;
	        printf("Multiplication is %d", z);
	        break;
	    }
	    default:
	    {
			printf("Wrong Input");
	    }
    }
}
```

better way of writing same code:

```c
#include <stdio.h>
#include <conio.h>
#include <stdlib.h>

void main()
{
	while(1)
	{
	    int ch, x, y, z;
	    printf("Press 1, Addtion\n");
	    printf("Press 2, Subtraction\n");
	    printf("Press 3, Multiplication\n");
	    printf("Enter your Choice: ");
	    scanf("%d", &ch);
	    switch (ch)
	    {
		    case 1:
		    {
		        printf("\nEnter 2 numbers: ");
		        scanf("%d %d", &x, &y);
		        z = x + y;
		        printf("Addition is %d\n", z);
		    }
		    case 2:
		    {
		        printf("Enter 2 numbers: ");
		        scanf("%d %d", &x, &y);
		        z = x - y;
		        printf("Subtraction is is %d\n", z);
		        break;
		    }
		    case 3:
		    {
		        printf("Enter 2 numbers: ");
		        scanf("%d %d", &x, &y);
		        z = x * y;
		        printf("Multiplication is %d\n", z);
		        break;
		    }
		    default:
		    {
				printf("Wrong Input\n");
		    }
	    }
	}
}
```

another way of writing same code:

```c
#include <stdio.h>
#include <conio.h>
#include <stdlib.h>

// functions start here //
void add()
{
	int x, y, z;
	printf("Enter 2 numbers: ");
	scanf("%d %d", &x, &y);
	z = x + y;
	printf("Addition is %d\n", z);
}

void sub()
{
	int x, y, z;
	printf("Enter 2 numbers: ");
	scanf("%d %d", &x, &y);
	z = x - y;
	printf("Subtraction is is %d\n", z);
}

void add()
{
	int x, y, z;
	printf("Enter 2 numbers: ");
	scanf("%d %d", &x, &y);
	z = x * y;
	printf("Multiplication is %d\n", z);
}

// main program  starts here //
void main()
{
	int ch;
	printf("Press 1, Addtion\n");
	printf("Press 2, Subtraction\n");
	printf("Press 3, Multiplication\n");
	printf("Press 4, exit\n");
	while(1)
	{
	    printf("\nEnter your Choice: ");
	    scanf("%d", &ch);
	    switch (ch)
	    {
		    case 1:
		    {
				add();
				break;
		    }
		    case 2:
		    {
				sub();
		        break;
		    }
		    case 3:
		    {
			    mul();
		        break;
		    }
			case 4:
			{
				exit();
			}
		    default:
		    {
				printf("Wrong Input\n");
		    }
	    }
	}
}

```