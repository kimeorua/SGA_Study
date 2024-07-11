# CodingTest

## 코딩테스트 문제 및 풀이

### 목차
+ ### [1. 0LV 문제 및 풀이](#0LV-문제-및-풀이)
+ ### [2. 1LV 문제 및 풀이]
+ ### [3. 2LV 문제 및 풀이]
+ ### [4. 3LV 문제 및 풀이]
+ ### [5. 4LV 문제 및 풀이]

## 0LV 문제 및 풀이
### 0LV부터 하는 이유
+ ### 코테를 처음 접해봤음으로, 문제의 출제 방식에 익숙해지기 위해여 0LV부터 시작.

#### 07.10 문제 및 풀이
+ #### 문제 1.
  + #### 문제: 정수 num1, num2가 주어질 때 num1, num2를 뺀 값을 return하도록 soltuion 함수를 완성해주세요.
  + #### 제한 사항: -50000 ≤ num1 ≤ 50000, -50000 ≤ num2 ≤ 50000
  + #### 답:
    ```cpp
    #include <stdio.h>
    #include <stdbool.h>
    #include <stdlib.h>
    
    int solution(int num1, int num2) {
        int answer = 0;
        if (num1 >= -50000 && num1 <= 50000 && num2 >= -50000 && num1 <= 50000)
        {
            answer = num1 - num2;
        }
        return answer;
    }
    ```
  + #### 풀이: num1, num2의 값을 if 문을 통해 조건에 부합 하는 지 확인 후, 부합하면 num1 - num2를 계산하여 answer에 저장하고, 반환 한다.

+ #### 문제 2.
  + #### 문제: 정수 num1과 num2가 매개변수로 주어집니다. 두 수가 같으면 1 다르면 -1을 retrun하도록 solution 함수를 완성해주세요.
  + #### 제한 사항: 0 ≤ num1 ≤ 10,000, 0 ≤ num2 ≤ 10,000
  + #### 답:
    ```cpp
    #include <stdio.h>
    #include <stdbool.h>
    #include <stdlib.h>
    
    int solution(int num1, int num2) {
        int answer = 0;
        
        if (num1 >= 0 && num1 <= 10000 && num2 >= 0 && num2 <= 10000)
        {
            answer = num1 == num2 ? 1 : -1;
        }
        
        return answer;
    }
    ```
  + #### 풀이: num1, num2의 값을 if 문을 통해 조건에 부합 하는 지 확인 후 부합하면 삼항 연산자를 통해 num1 과 num2가 같은지 비교하여 answer에 1, -1을 저장한 후 반환 한다.

+ #### 문제 3.
  + #### 문제: 직각삼각형이 주어졌을 때 빗변의 제곱은 다른 두 변을 각각 제곱한 것의 합과 같습니다.직각삼각형의 한 변의 길이를 나타내는 정수 a와 빗변의 길이를 나타내는 정수 c가 주어질 때, 다른 한 변의 길이의 제곱, b_square 을 출력하도록 한 줄을 수정해 코드를 완성해 주세요.
  + #### 제한 사항: 1 ≤ a < c ≤ 100, 1줄만 수정하여 버그를 고치세요.
  + #### 답:
    ```cpp
    int main(void) {
      int a;
      int c;
      cin >> a >> c;
      
      int b_square = c*c - a*a; // 수정전: int b_square = c - a;
      cout << b_square << endl;
      return 0;
    }
    ```
  + #### 풀이: 피타고라스의 정리를 이용하여 a*a + b*b = c*c 임으로 b*b = c*c - a*a임으로 해당 방식으로 코드를 변경 함
