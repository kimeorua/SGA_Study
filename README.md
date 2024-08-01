# SGA 국비 교육 정리 및 코테

# 목차
+ ## [1. 국비 교육 정리](#SGA-국비-교육-내용-정리)
+ ## [2. 코테](#코딩테스트-문제-및-풀이)

## SGA 국비 교육 내용 정리
+ ### 24_07_24
  + #### 교육 내용: 무기 충돌 처리 및 데미지 처리 방식.
    + #### WeaponComponent에 델리게이트를 이용하여 Collision->OnComponentBeginOverlap을 호출하여 충돌 및 데미지 처리를 시작함.
    + #### HP와 같은 정보는 StatusComponent에서 F_Status 구조체의 변수를 가지고 있으며 해당 구조체는 현재HP 최대HP를 가지고 있음
    + #### 현재 상태를 체크하는 StateComponent를 작성하고 E_State열거형을 통해 현재 상태를 확인 하여 정보를 처리함.
    + #### 머테리얼 인스턴스를 활용하여 피격 시 캐릭터의 머테리얼 색상이 변경 되도록 구현함.
   
+ ### 24_07_25
  + #### 교육 내용: 피격 모션 출력
    + #### 피격된 방향에 따라 피격 모션이 다르게 출력되도록 구현 (EX: 플레이어과 왼쪽에서 때리면 왼쪽에서 맞은 모션이 나오도록 구현함)
    + #### 공격한 객체의 owner와 피격된 객체의 거리를 구한 후 해당거리와, 피격된 객체의 Rotation을 통해 CalculateDirection함수를 사용하여 회전 값을 계산 Yaw값을 활용함
    + #### 또한 피격모션 배열의 길이를 구한후, 360 / 배열의 길이를 통해 한 방향이 가지는 각도를 계산 후 저장함.
    + #### 배열의 길이가 1보다 크다면 전체 각도를 -180 ~ 180에서 0~360으로 변경하기 위해 계산된 Yaw값에 + 360을 더한 후 나머지 계산을 360으로 계산 하여 나머지를 기준으로 각도를 계산 함.
    + #### 그후 계산한 각도 / 한 방향이 가지는 각도를 계산하여 배열 index을 반환한다.
    + #### 반환한 index를 BaseCharacter의 데미지 처리 이벤트에서 호출하여 애님 몽타주를 출력 한다
      
+ ### 24_07_30
  + #### 교육 내용: 캐릭터 사망시 상태를 Ragdoll로 변경 및 일정 시간 후 제거
    + #### BaseCharacter에서 함수를 작성, 피직스시뮬레이트를 키고, 캡슐 콜리전은 Pawn무시로, 메쉬는Ragdoll로 변경
    + #### 변경 완료후 Timer를 활용하여 일정 시간 후 OnDestroy함수가 실행 되도록 구현 함
    + #### 해당 함수를 AnimNotify에서 호출하여, 원하는 타이밍에 변경 하도록 구현 함.
    + #### 추가적으로 Ragdoll로변경시 혹시 모를 상황을 대비하여 애니메이션을 중지 하도록 개선 함.
      
  + #### 교육 내용: 스킬 사용 시 파티클 스폰
    + #### WeaponComponent에서 함수를 작성, 파티클이 스폰될때 플레이어 캐릭터의 현재 좌표를 기준으로 전방 벡터를 구함
    + #### 해당 벡터를 분해후,  z좌표는 캡슐컴포넌트의 길이의 절반 만큼 캐릭터의 중심 좌표에서 더해 캐릭터의 머리 위치 좌표를 구함
    + #### 그후 캐릭터의 하향 벡터를 구한 후 일정 수치를 곱하여 스폰될 수 있는 한계지점까지 LineTrace를 활용하여 바닥을 체크 함. 
    + #### 바닥이 있으면 해당 지점에 파티클을 스폰 함.
   
+ ### 24_08_01
  + #### 교육 내용: 스킬 사용 시 무기에 트레일 출력
    + #### 스킬 사용 시 무기에 트레일이 나오게 하도록 구현 하기위해, AnimnotifyState를 상속받아 ANS_Trail을 작성 함
    + #### AnimnotifyState에서는 Set을 활용하여 변수를 저장 할수 없으므로 BaseWeapon에 트레일을 제어 하기 위한 "파티클 시스템 위치 사용" 형의 변수를 추가함
    + #### AnimnotifyState Begin에서 SpawnEmiterAttach()함수를 통해 스폰 및 부착하고, BeginTrails함수를 통해 트래일을 재생 시키도록 구현함.
    + #### AnimnotifyState End에서 BaseWeapon에저장된 변수를 통해 EndTrails함수를 호출 하여 트레일을 종료 하도록 구현함
      
## 코딩테스트 문제 및 풀이

### 레벨 별 풀이
+ ### [1. 0LV 문제 및 풀이](#0LV-문제-및-풀이)
+ ### [2. 1LV 문제 및 풀이](#1LV-문제-및-풀이)
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
 
  + #### 문제 4.
  + #### 문제: 여름이는 강아지를 산책시키려고 합니다. 여름이는 2차원 좌표평면에서 동/서/남/북 방향으로 1m 단위로 이동하면서 강아지를 산책시킵니다. 산책루트가 담긴 문자열 route가 주어질 때, 도착점의 위치를 return하도록 빈칸을 채워 solution함수를 완성해 주세요.
    + #### route는 "N", "S", "E", "W"로 이루어져 있습니다.
    + #### "N"은 북쪽으로 1만큼 움직입니다.
    + #### "S"는 남쪽으로 1만큼 움직입니다, 북쪽으로 -1만큼 움직인 것과 같습니다.
    + #### "E"는 동쪽으로 1만큼 움직입니다.
    + #### "W"는 서쪽으로 1만큼 움직입니다, 동쪽으로 -1만큼 움직인 것과 같습니다.
    + #### 출발점으로부터 [동쪽으로 떨어진 거리, 북쪽으로 떨어진 거리]형태로 강아지의 최종 위치를 구해서 return해야 합니다.
    + #### 출발점을 기준으로 서쪽, 남쪽에 있는 경우는 동쪽, 북쪽으로 음수만큼 떨어진 것으로 표현합니다.
    + #### 출발점으로부터 동쪽으로 2, 북쪽으로 3만큼 떨어졌다면 [2, 3]을 return 합니다.
    + #### 출발점으로부터 서쪽으로 1, 남쪽으로 4만큼 떨어졌다면 [-1, -4]를 return 합니다.
  + #### 제한 사항: 1 ≤ route의 길이 ≤ 2, route는 "N", "S", "E", "W"로만 이루어져 있습니다, 빈칸 채우기
  + #### 답:
    ```cpp
    #include <string>
    #include <vector>
    using namespace std;
    vector<int> solution(string route) {
        int east = 0;
        int north = 0;
        vector<int> answer(2);
        for(int i=0; i<route.length(); i++){
            switch(route[i]){
                case 'N':
                    north++;
                    break;
                case 'S':
                    north--; #빈칸
                    break;
                case 'E':
                    east++; #빈칸
                    break;
                case 'W':
                    east--; #빈칸
                    break;  #빈칸
            }
        }
        answer[0] = east;
        answer[1] = north;
        return answer;
    }
    ```
  + #### 풀이: 북쪽으로 이동한 거리를 north, 동쪽으로 이동한 거리를east에 각각 저장하여, N = north + 1, S = north - 1, E = east + 1, W = east - 1을 적용하여 해결 함


## 1LV 문제 및 풀이

+ #### 문제 1.
  + #### 문제: 빈 병 a개를 가져다주면 콜라 b병을 주는 마트가 있을 때, 빈 병 n개를 가져다주면 몇 병을 받을 수 있는지 계산하는 함수를 구현 하라. 단, 보유 중인 빈 병이 a개 미만이면, 추가적으로 빈 병을 받을 순 없다.
  + #### 제한 사항: 1 ≤ b < a ≤ n ≤ 1,000,000, 정답은 항상 int 범위를 넘지 않게 주어집니다.
  + #### 답:
    ```cpp
    #include <string>
    #include <vector>
    
    using namespace std;
    
    int solution(int a, int b, int n) {
        int answer = 0;
        int current = n;
        while(current >= a)
        {
            int set = current / a;
            int give = set * a;
            int gain = set * b;
            current = current - give + gain;
            answer += gain;
        }
        
        return answer;
    }
    ```
  + #### 풀이: 현재 병을 current에 저장하고, 빈병의 묶음을 계산하여, 가져가는 빈병과, 얻어가는 빈병을 계산, current - give + gain를 계산하여 조건을 확인후, answer에 더하여 반환 한다.

  + #### 문제 2.
    + #### 문제: 자연수 n이 매개변수로 주어집니다. n을 x로 나눈 나머지가 1이 되도록 하는 가장 작은 자연수 x를 return 하도록 solution 함수를 완성해주세요. 답이 항상 존재함은 증명될 수 있습니다.
    + #### 제한 사항: 3 ≤ n ≤ 1,000,000
    + #### 답:
      ```cpp
      #include <string>
      #include <vector>
      
      using namespace std;
      
      int solution(int n) {
          int answer = 0;
          vector<int> numV;
          for (int i = n - 1 ; i > 0; i --)
          {
              if (n % i == 1) 
              {
                  numV.push_back(i);
              }
          }
          answer = numV.back();
          return answer;
      }
      ```
    + #### 풀이: for 반복문을 통해 n-1 부터 1 까지의 수로 나머지를 계산, 나머지가 1인 i만 vector에 push_back함수를 통해 저장한다. 그후 가장 끝부분의 원소를 반환하면 가장 작은 수가 나온다.
   
  + #### 문제 3.
  + #### 문제: 정수를 담고 있는 배열 arr의 평균값을 return하는 함수, solution을 완성해보세요.
  + #### 제한 사항: arr은 길이 1 이상, 100 이하인 배열입니다, arr의 원소는 -10,000 이상 10,000 이하인 정수입니다.
  + #### 답:
    ```cpp
    #include <string>
    #include <vector>
    
    using namespace std;
    
    double solution(vector<int> arr) {
        double answer = 0;
        int count = 0;
        
        for (int x : arr)
        {
            answer += x;
            count ++;
        }
        
        return answer / count;
    }
    ```
  + #### 풀이: 배열의 첫번째 인수부터 answer에 더한후 count를 늘려 최종적으로 answer / count를 반환 한다.
 
  + #### 문제 4.
  + #### 문제: 그리워하는 사람의 이름을 담은 문자열 배열 name, 각 사람별 그리움 점수를 담은 정수 배열 yearning, 각 사진에 찍힌 인물의 이름을 담은 이차원 문자열 배열 photo가 매개변수로 주어질 때, 사진들의 추억 점수를 photo에 주어진 순서대로 배열에 담아 return하는 solution 함수를 완성해주세요.
  + #### 제한 사항: 3 ≤ name의 길이 = yearning의 길이≤ 100, 3 ≤ name의 원소의 길이 ≤ 7, name의 원소들은 알파벳 소문자로만 이루어져 있습니다, name에는 중복된 값이 들어가지 않습니다.
  + #### 1 ≤ yearning[i] ≤ 100
  + #### yearning[i]는 i번째 사람의 그리움 점수입니다.
  + #### 3 ≤ photo의 길이 ≤ 100
  + #### 1 ≤ photo[i]의 길이 ≤ 100
  + #### 3 ≤ photo[i]의 원소(문자열)의 길이 ≤ 7
  + #### photo[i]의 원소들은 알파벳 소문자로만 이루어져 있습니다.
  + #### photo[i]의 원소들은 중복된 값이 들어가지 않습니다.
  + #### 답:
    ```cpp
    #include <string>
    #include <vector>
    
    using namespace std;
    
    vector<int> solution(vector<string> name, vector<int> yearning, vector<vector<string>> photo) {
        vector<int> answer;
        for (vector arr : photo)
        {
            int point = 0;
            for (string n : arr)
            {
                for (int i = 0; i < name.size(); i++)
                {
                    if (n == name[i])
                    {
                        point += yearning[i];
                    }
                }
            }
            answer.push_back(point);
        }
        return answer;
    }
    ```
  + #### 풀이: 2중배열을 탐색하여, name과 비교후 해당 인댁스 번호와 같은 yearning의 값을 point에 합산, 한 배열이 끝나면 저장한후, 모든 탐색이 끝나면 반환 함.
