# Emotion 9차시 동아리 과제
### 1. c언어로 stack 구현하기
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
   
### 2. c언어로 큐 구현하기
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
### 3. c언어로 백터 구현하기
```
#include <stdio.h>
#include <stdlib.h>

typedef struct {
    int *data;
    int size;
    int capacity;
} Vector;

void vector_init(Vector *vector) {
    vector->size = 0;
    vector->capacity = 4;
    vector->data = (int *)malloc(vector->capacity * sizeof(int));
}

void vector_add(Vector *vector, int value) {
    if (vector->size == vector->capacity) {
        vector->capacity *= 2;
        vector->data = (int *)realloc(vector->data, vector->capacity * sizeof(int));
    }
    vector->data[vector->size++] = value;
}

void vector_free(Vector *vector) {
    free(vector->data);
}

int main() {
    Vector vector;
    vector_init(&vector);

    for (int i = 1; i <= 5; i++)
        vector_add(&vector, i);

    for (int i = 0; i < vector.size; i++)
        printf("%d ", vector.data[i]);
    printf("\n");

    vector_free(&vector);
    return 0;
}
```
일단 백터를 구현하기 typedef struct를 통해 백터를 구현하기 위해 필요한 배열, 요소의 수, 최대로 가질 수 있는 요소의 수를 선언한 후, vector_init에서 배열 크기를 0으로 지정하여, 비어 있는 것을 나타내고, 수용 가능한 공간을 4로 지정하여 4개까지 들어올 수 있게 한후, malloc을 통해 4개에 대한 메모리 공간을 할당한다. 그리고 vector_add에서 데이터를 집어넣고 백터가 가득 차면 용량이 2개 늘어나게 하고, vector_free를 통해 메모리를 해제해주었다.
### 4. 단일 링크드 리스트 개념
단일 링크드 리스트는 각 노드가 데이터와 다음 노드를 가리키는 포인터를 가지고 있는 선형 자료구조이다. 리스트의 시작점은 "헤드"라 불리며, 리스트의 끝은 다음 노드가 없는 노드로 표시된다.
#### 구조
단일 링크드 리스트의 각 노드는 다음과 같이 구성한다.
* 데이터(Data) : 노드가 저장하는 값
* 포인터(Next) : 다음 노드를 가리키는 포인터
[Data | Next] -> [Data | Next] -> [Data | Next] -> None
#### 기본 연산
1) 삽입

   (1) 리스트의 처음에 삽입
   
   (2) 리스트의 끝에 삽입
   
   (3) 리스트의 특정 위치에 삽입
3) 삭제
   
   (1) 특정 값을 가진 노드 삭제
   
   (2) 리스트의 처음 노드 삭제
   
   (3) 리스트의 끝 노드 삭제
5) 탐색
   
   (1) 특정 값을 가진 노드 탐색
7) 출력
   
   (1) 리스트의 모든 요소 출력

#### 장단점
1) 장점

   (1) 크기가 동적으로 조절되어, 메모리 사용이 효율적이다.
   
   (2) 리스트의 앞이나 뒤에서 삽입과 삭제가 빠르다.
3) 단점
   
   (1) 각 노드가 데이터와 포인터를 저장하기 때문에 추가적인 메모리 사용이 필요하다.

* 참고 자료는 많아서 여기에 다 적기는 무리가 있어서 못 적었음에 대한 양해를 부탁드립니다.
