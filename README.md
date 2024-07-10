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
+ #### 문제 2.
