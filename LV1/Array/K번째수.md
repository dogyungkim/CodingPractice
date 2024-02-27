###### 문제 설명
배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하려 합니다.

예를 들어 array가 [1, 5, 2, 6, 3, 7, 4], i = 2, j = 5, k = 3이라면
1. array의 2번째부터 5번째까지 자르면 [5, 2, 6, 3]입니다.
2. 1에서 나온 배열을 정렬하면 [2, 3, 5, 6]입니다.
3. 2에서 나온 배열의 3번째 숫자는 5입니다.

배열 array, [i, j, k]를 원소로 가진 2차원 배열 commands가 매개변수로 주어질 때, commands의 모든 원소에 대해 앞서 설명한 연산을 적용했을 때 나온 결과를 배열에 담아 return 하도록 solution 함수를 작성해주세요.

##### 제한사항
- array의 길이는 1 이상 100 이하입니다.
- array의 각 원소는 1 이상 100 이하입니다.
- commands의 길이는 1 이상 50 이하입니다.
- commands의 각 원소는 길이가 3입니다.

 ##### 입출력 예
|array|commands|return|
|---|---|---|
|[1, 5, 2, 6, 3, 7, 4]|[[2, 5, 3], [4, 4, 1], [1, 7, 3]]|[5, 6, 3]|
### 나의 답
- 배열 인덱싱 후 정렬이라 어렵지는 않은 문제였다.
```swift
import Foundation

func solution(_ array:[Int], _ commands:[[Int]]) -> [Int] {
    return commands.map{
        var x = array[$0[0]-1..<$0[1]].sorted()
        return x[$0[2]-1]
    }
}
```

### 남의 답
- 굳이 x라는 변수를 안 만들고 바로 return 해버리는 생각!
```swift
import Foundation
    func solution(_ array:[Int], _ commands:[[Int]]) -> [Int] {
        return commands.map({(key) in
            return array[(key[0]-1)...(key[1]-1)].sorted()[key[2]-1]
        })

    }
```