Emotion 12차시 동아리 과제
1. c언어로 stack 구현하기
```
#include <stdio.h>
#define SIZE 1000 
 
int stack[SIZE];    
int first = -1;   
 
int check_full(){
    if(first >= SIZE -1){    
        printf("스택이 가득 찼습니다.\n");
        return 1;
    }
    return 0;
}
int check_empty(){
    if(first == -1){
        printf("스택이 비어 있습니다.\n");
        return 1;
    }
    return 0;
}
 
void push(int data){
    if(!check_full()){
        first++;
        stack[first] = data;
    }
} 
 
int pop(){
    if(!check_empty()){
        return stack[first--];
    }
}
 
void Stack(){
    int i;
    for(i=0; i<=first; i++){
        printf("%d ", stack[i]);
    }
    printf("\n");
}
 
int main(){
    
    push(5);
    push(4);
    push(3);
    push(2);
    push(1);
    Stack();
    pop();
    Stack();
    
    return 0;
}
```
우선 배열의 크기를 선언한 후, stack을 효율적으로 구현하기 위해 맨 위에 있는 값(비어 있는 값)은 -1로 설정한 후, check_full을 통해 빈 값이 size - 1보다 크면 가득 찼다고 출력하고, 아니면 0을 반환하게 하였다. 그리고 check_empty를 통해 first가 빈 값이면 스택이 비어있다고 출력하고, 아니면 0을 반환하게 하였다. 그리고 push를 통해 값을 넣게 하고, Stack을 통해 pop을 구현하였다. 
   
