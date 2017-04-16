## Copy a string by using pointers in c 

The below example is to use pointers to copy a string in c. When I was a beginner in c I was afraid to use pointers in my code because it is hard to use it. However, it is a charming method, if we understand it a lot, it becomes more charming. The CopyString is a function to copy a string to a empty string. The idea is simple, but it is easy to make a mistake.  <br /> 
<br />
------------------

The target is the destination where we want to copy a string to. <br />
The source is a string that I want to copy to the destination.  <br />
Here I claim a pointer `start_pointer` for setup the start pointer for target. `start_pointer` is very important in this function. If we don't claim a pointer that pointer to the beginning of target, it could cause a problem.  <br />  

```c
char *CopyString(char *target, char *source){

  char *start_pointer;
  start_pointer = target;
  
  while (*source != '\0') {     
    	*target = *source;
    	printf("target [%s]\n",target );
    	source++;
    	target++;

    }
  *target = '\0';
  
  return start_pointer,
}

```
`printf("target [%s]\n",target );` this line will print out: 

```c
target [H]
target [e]
target [l]
target [l]
target [o]
target [ ]
target [W]
target [o]
target [r]
target [l]
target [d]
```





```c
int main(int argc, char const *argv[])
{
  char *str1="Hello World"; 
  char *target;
  target = malloc((100+1)*sizeof(char*));
  char *result;
  
  
}


```
