Emotion 9차시 동아리 과제
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
   
2. 큐 구현
```
#include <stdio.h>
#define SIZE 100

int que[SIZE];
int front = -1;
int rear = -1;

void inque(int data) {
    if (rear == SIZE - 1) {
        printf("가득 찼습니다.\n");
        return;
    }
    que[++rear] = data;
}

int deque() {
    if (front == rear) {
        printf("큐가 비어있습니다.\n");
        return -1;
    }
    return que[++front];
}

int main() {
    inque(3);
    inque(2);
    inque(1);

    printf("%d\n", deque()); 
    printf("%d\n", deque()); 
    printf("%d\n", deque()); 

    return 0;
}
```
일단 배열 선언을 편하게 하기 위해 # define ~을 통해 배열의 크기를 선언한 후, 큐 배열을 선언한 후, 큐 앞 뒤에 빈 값을 표현하기 위해 front와 rear을 선언한 후 -1을 대입한다. 그리고 inque를 통해 rear와 size-1이 같은지를 보는 것은 꽉 찬 것인지 확인하는 것이고, deque는 front와 rear가 같은 지를 통해 비어있는지를 확인하는 것이다. 그리고 main에서 출력해보면 잘 구현이 된 것을 알 수 있다.
3. 백터 구
