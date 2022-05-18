# 이진탐색 알고리즘

> 중간값을 임의로 선택하고, 중간값과 찾고자 하는 특정값의 대/소 비교를 통해 특정값을 찾는 알고리즘.  
이진 탐색을 할 배열은 **항상 순서대로 정렬**되어 있어야 한다! (대/소 비교를 위해)

<br>

## 💡 이진 탐색 구현 코드

```java
public int search(int[] nums, int target) {
    int start = 0;
    int end = nums.length - 1;
    while (start <= end) {
        // pivot : 기준점. 소숫점 이하는 버림
        // (end - start) : integer overflow 방지
        int pivot = start + (end - start) / 2;

        if (nums[pivot] == target) return pivot; // 찾으면 return

        if (target < nums[pivot]) end = pivot - 1; // 작으면 end를 이동
        else start = pivot + 1; // 크면 start를 이동
    }
    return -1; // 찾기 실패
}
```  

<br>

## 💡 자바 이진탐색 라이브러리

>  **Arrays.binarySearch((정렬된)배열, 찾을값)** 라이브러리를 이용!

binarySearch() 메서드가 해당 값이 존재하면 인덱스 번호를 반환하고, 그렇지 않으면 음수를 반환한다고만 알고있었다.😱  
**But**, 반환되는 음수에 "니가 찾는값은 없는데, 만약에 이 배열에 그 값을 넣고싶으면 넣어야 되는 위치는 여기야!" 라는 힌트가 숨어있었다!

<br>

예를들어, 
>int[] nums = [1,3,5,6], int target = 2 일때

<img src="https://user-images.githubusercontent.com/10507836/169006132-fdb95fba-4787-482a-9201-1d7ec78254ee.jpg" />

<br>

즉, 
target값이 존재하면 그 값의 인덱스를 반환하고,  
**존재하지 않으면 그 값을 배열에 끼워 넣어 <span style="color:blue">1부터 시작하는 인덱스를 음수로 변경하여 반환</span>**한다!