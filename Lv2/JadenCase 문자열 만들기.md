---
푼날자: 2024-02-27
tags:
  - lv2
  - 구현
정답률: 78%
---
###### 문제 설명

JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다. 단, 첫 문자가 알파벳이 아닐 때에는 이어지는 알파벳은 소문자로 쓰면 됩니다. (첫 번째 입출력 예 참고)  
문자열 s가 주어졌을 때, s를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.
##### 제한 조건
- s는 길이 1 이상 200 이하인 문자열입니다.
- s는 알파벳과 숫자, 공백문자(" ")로 이루어져 있습니다.
    - 숫자는 단어의 첫 문자로만 나옵니다.
    - 숫자로만 이루어진 단어는 없습니다.
    - 공백문자가 연속해서 나올 수 있습니다.
##### 입출력 예

|s|return|
|---|---|
|"3people unFollowed me"|"3people Unfollowed Me"|
|"for the last week"|"For The Last Week"|

### 나의 답
- map 두번 joined 두번 쓰는게 맘이 불편...!
- 공백으로 나누고, 나눠진 array의 각 문자열의 첫 글자는 대문자, 그외는 소문자로 바꾸고, 다시 공백을 넣어주면서 더해줘서 하나의 문자열로 만듬
```swift
func solution(_ s:String) -> String {
   var answer = s.components(separatedBy: " ")
            .map{ $0.enumerated().map{ 
                $0.offset == 0 ? $0.element.uppercased() : $0.element.lowercased()
            }.joined()
                }.joined(separator: " ")
    return answer
}
```

### 남의 답
- 문자열을 반복문으로 접근 후, 새로운 문자열에 저장하는 방법!
```swift
func solution(_ s:String) -> String {
    var ans = ""
    var index = 0

    for char in s {
        if char != " " {
            if index == 0 {
                ans += String(char).uppercased()
            } else {
                ans += String(char).lowercased()
            }
            index += 1
        } else {
            ans += " "
            index = 0
        }
    }
    return ans
}
```

### 실행 속도
|   |   |
|---|---|
|테스트 1 〉|통과 (0.15ms, 16.5MB)|
|테스트 2 〉|통과 (0.20ms, 16.4MB)|
|테스트 3 〉|통과 (0.19ms, 16.3MB)|
|테스트 4 〉|통과 (0.20ms, 16.5MB)|
|테스트 5 〉|통과 (0.24ms, 16.1MB)|
|테스트 6 〉|통과 (0.32ms, 16.2MB)|
|테스트 7 〉|통과 (0.19ms, 16.2MB)|
|테스트 8 〉|통과 (0.15ms, 15.9MB)|
|테스트 9 〉|통과 (0.24ms, 16.5MB)|
|테스트 10 〉|통과 (0.10ms, 16MB)|
|테스트 11 〉|통과 (0.37ms, 16.3MB)|
|테스트 12 〉|통과 (0.19ms, 16.4MB)|
|테스트 13 〉|통과 (0.18ms, 16.1MB)|
|테스트 14 〉|통과 (0.21ms, 16.3MB)|
|테스트 15 〉|통과 (0.39ms, 16.1MB)|
|테스트 16 〉|통과 (0.14ms, 16.1MB)|
|테스트 17 〉|통과 (0.24ms, 16.4MB)|
|테스트 18 〉|통과 (0.12ms, 16MB)|