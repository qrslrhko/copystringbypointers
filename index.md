## Copy a string by using pointers in c 



The below example is to use pointers to copy a string in c. When I was a beginner in c I was afraid to use pointers in my code because it is hard to use it. However, if we understand it a lot, it becomes more charming. The CopyString is a function to copy a string to a empty string. The idea is simple, but it is easy to make a mistake.  <br /> 
<br />

The `target` is the destination where we want to copy a string to. <br />
The `source` is a string that I want to copy to the destination.  <br />
Here I claim a pointer `start_pointer` for setup the start pointer for `target`. `start_pointer` is very important in this function. If we don't claim a pointer that pointer to the beginning of `target`, it could cause a problem.  <br />  

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
  
  return start_pointer;
}

```

```c   
source: | H | e | l | l | o |   | W | o | r | l | d |'\0'|
target: |   |   |   |   |   |   |   |   |   |   |   |    |.......|
          ↑
start_pointer pointers to the beginning of target


---while loop---
target: | H |   |   |   |   |   |   |   |   |   |   |    |.......|
          ↑
          target pointer
target: | H | e |   |   |   |   |   |   |   |   |   |    |.......|
              ↑
          target pointer
target: | H | e | l |   |   |   |   |   |   |   |   |    |.......|  
                  ↑
            target pointer
target: | H | e | l | l |   |   |   |   |   |   |   |    |.......|   
                      ↑
               target pointer
target: | H | e | l | l | o |   |   |   |   |   |   |    |.......|    
                          ↑
                     target pointer
target: | H | e | l | l | o |   | W |   |   |   |   |    |.......| 
                              ↑
                        target pointer
target: | H | e | l | l | o |   | W | o |   |   |   |    |.......|    
                                  ↑
                            target pointer
target: | H | e | l | l | o |   | W | o | r |   |   |    |.......|   
                                      ↑
                                target pointer
target: | H | e | l | l | o |   | W | o | r | l |   |    |.......|   
                                          ↑
                                    target pointer
target: | H | e | l | l | o |   | W | o | r | l |   |    |.......|   
                                              ↑
                                        target pointer
target: | H | e | l | l | o |   | W | o | r | l | d |    |.......|   
                                                  ↑
                                            target pointer
---out of loop---


target: | H | e | l | l | o |   | W | o | r | l | d |'\0'|.......|          // *target = '\0';
                                                      ↑
                                                    target are here. Give null character represent termination of string  
```                                                    
            
Because I want to return this copying string we have to return `start_pointer`. This pointer points to the beginning of destination. If we return `target` pointer, it will point out nothing becuase it is in the end of detination. <br />               
            
In the main function, we allocate a space of dentination string by `malloc`.  <br />                                                   
                                                    
```c
int main(int argc, char const *argv[])
{
  char *str1="Hello World"; 
  char *target;
  target = malloc((100+1)*sizeof(char*));
  char *result;
  result = CopyString(target,str1);
  printf("<%s>\n",result );
  
}


```
