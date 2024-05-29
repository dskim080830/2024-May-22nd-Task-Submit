# 2024-May-22nd-Task-Submit
1) 초콜릿 자르기(2163번)

   
#include <stdio.h>
int main()
{
    int N, M;
    scanf("%d %d", &N, &M);
    printf("%d", N * M - 1);
}
N과 M을 입력받고, N * M - 1이 최솟값인 것을 구해내서 답을 출력하게 했다.
2) 손가락 게임(31866번)


#include <stdio.h>

int main() {
    int j_f, y_f;
    scanf("%d %d", &j_f, &y_f);
    
    if ((j_f != 0 && j_f != 2 && j_f != 5) && (y_f != 0 && y_f != 2 && y_f != 5)) {
        printf("=");
    } else if (j_f != 0 && j_f != 2 && j_f != 5) {
        printf("<");
    } else if (y_f != 0 && y_f != 2 && y_f != 5) {
        printf(">");
    } else if (j_f == y_f) {
        printf("=");
    } else if ((j_f == 0 && y_f == 2) || (j_f == 2 && y_f == 5) || (j_f == 5 && y_f == 0)) {
        printf(">");
    } else if ((j_f == 2 && y_f == 0) || (j_f == 5 && y_f == 2) || (j_f == 0 && y_f == 5)) {
        printf("<");
    }
    
    return 0;
}
가위바위보 2개를 입력받고, if와 else if를 이용해 문제를 풀었다.
3) 과민성 대장 증후군(31831번)


#include <stdio.h>

int main() {
    int N, M;
    scanf("%d %d", &N, &M);

    int A[N];
    for (int i = 0; i < N; i++) {
        scanf("%d", &A[i]);
    }

    int stress = 0;
    int count = 0;

    for (int i = 0; i < N; i++) {
        if (A[i] >= 0) {
            stress += A[i];
        } else {
            stress += A[i]; 
            if (stress < 0) {
                stress = 0;
            }
        }

        if (stress >= M) {
            count++;
        }
    }

    printf("%d\n", count);
    return 0;
}
for문과 if문을 써서 문제를 풀었다.
4) 버블버블(31870번)


#include <stdio.h>
int main()
{
   int N;
   int temp;
   scanf("%d", &N);
   int A[N];
   int i = 0;
   int j = 0;
   int count = 0;
   int count1 = 1;
   for (i = 0; i < N; i++) {
       scanf("%d", &A[i]);
   }
   int B[N];
   for (i = 0; i < N; i++) {
       B[i] = A[i];
       
   }
   for (i = 0; i < N; i++) {
  
       for(j = 0; j < N-1; j++) {
           if (A[j] > A[j+1]) {
               temp = A[j];
               A[j] = A[j+1];
               A[j+1] = temp;
               count += 1;
           }
       }
   }
     for (i = 0; i < N; i++) {
    
       for(j = 0; j < N-1; j++) {
           if (B[j] < B[j+1]) {
               temp = B[j];
               B[j] = B[j+1];
               B[j+1] = temp;
               count1 += 1;
           }
       }
   }
   if (count < count1)
       printf("%d", count);
   else
       printf("%d", count1);
   return 0;
}
for문으로 정렬을 구현하고, 그것을 또 역순으로 정렬을 구현해서 문제를 풀었다.
5. 마라탕후루(31923번)
#include <stdio.h>


int N, P, Q;
int A[1000], B[1000], answer[1000];

int main() {

    
    scanf("%d %d %d", &N, &P, &Q);
    for (int i = 0; i < N; ++i) {
        scanf("%d", &A[i]);
    }

   
    for (int i = 0; i < N; ++i) {
        scanf("%d", &B[i]);
    }

    
    for (int i = 0; i < N; ++i) {
        int a = A[i];
        int b = B[i];
        int j = 0;

        while (a != b) {
            a += P;
            b += Q;
            ++j;

            if (j == 10000) {
                printf("NO");
                return 0;
            }
        }

        answer[i] = j;
    }

    printf("YES\n");

    for (int i = 0; i < N; ++i) {
        printf("%d ", answer[i]);
    }

    return 0;
}
for문과 while문을 이용해 풀었고, 만약 10000번 돌려도 안 되면 No, 아니면 Yes를 출력하게 하였다.
