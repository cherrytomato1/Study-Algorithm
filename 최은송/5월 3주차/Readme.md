# 5월 3주차 풀이
## 1. BOJ G5 16234 인구이동 👩‍🦽
### 문제 정의
1. N*N 크기 땅에 국경선을 공유하는 두 나라의 인구 차이가 L 이상, R 이하면 국경선을 열고 인구 이동을 시작한다.
2. 국경선을 연 나라들은 연합국이 되어 각 칸의 인구수가 (연합의 인구수) / (연합을 이루고 있는 칸의 개수)가 된다.
3. 위의 방법으로 인구 이동이 없을 때까지 인구이동을 할 때 , 인구 이동이 몇 번 발생하는지 출력하시오

### 문제 풀이
1. while문으로 연합국이 하나도 없을때까지 반복
2. N*N을 반복으로 탐색, 한번 반복할때마다 return+1
3. 아직 방문하지 않은 칸은 bfs로 연합국. L 이상 R 이하면 sum에 더하고 cnt + 1로 개수를 세어준다. 연합국 좌표는 따로 큐에 저장한다.
4. bfs의 탐색이 끝나고 cnt가 1 이상이면 평균 인구를 구해서 큐에 저장된 연합국 좌표에 set해준다.

### 정리
인구이동수가 맵을 탐색하는 횟수라고 생각 못하고 한 연합국마다 수라고 생각해서 애를 먹었다. 구현치고는 까다롭지 않은 문제였다. 연합국 좌표를 deque로 안하고 list로 했어도 됐을 것 같다.

----

## 2. BOJ G3 8913 문자열뽑기 🗳
### 문제 정의
1. a, b로만 이루어진 문자열 s에서 2 이상의 연속 부분 문자열을 제거하고 합치는 작업을 할 때 빈 문자열로 바꿀 수 있으면 1, 없으면 0을 출력하라
2. 문자열 길이 1 이상, 25 이하

### 문제 풀이
1. 재귀적으로 연속 문자열을 제거한 substring을 넘겨서 빈 문자열이면 true 리턴, 아니면 false 리턴
2. 0부터 문자열 길이-1 탐색해서 부분 문자열을 찾음.
3. 연속된 문자열을 제거한 나머지 문자열을 substring으로 자르고 합쳐서 다시 재귀함수로 보냄. substring(0, start) + substring(end, s,length())
4. 기저조건으로 s.length() == 0, 빈 문자열이면 return true
5. 만약 문자열의 처음부터 끝까지 탐색을 마쳤는데 리턴하지 않았다면 빈 문자열을 만들지 못하는 것이므로 return false
```java
static boolean dfs(String s) {
    if(s.length() == 0) {
        return true;
    }
    int i = 0;
    int len = s.length();
    while(i < len - 1) {
        if(s.charAt(i) == s.charAt(i+1)) {
            int start = i;
            while(i < len-1 && s.charAt(i) == s.charAt(i+1)) {
                i++;
            }
            i++;
            int end = i;
            StringBuilder sb = new StringBuilder();
            sb.append(s.substring(0, start)).append(s.substring(end, len));
            
            if(dfs(sb.toString()))
                return true;
        }
        else	i++;
    }
    return false;
}
```


### 정리
인덱스 처리가 역시나 헷갈렸다. 문제를 정리하면서 보니 문자열은 무조건 a, b로만 나누어져 있으므로 비트마스킹 처리로 풀면 시간과 메모리를 더 줄일 수 있을 것 같다. 

---
## 3. BOJ G2 16472 고냥이 🐱
### 문제 정의
1. 문자열과 인식할 수 있는 알파벳의 최대 개수 N이 주어진다.
2. 번역기가 인식할 수 있는 문자열의 최대길이를 출력하시오
3. 1 < N ≤ 26, 1 ≤ 문자열의 길이 ≤ 100,000

### 문제 풀이
1. 투포인터 문제
2. r이 문자열을 한칸씩 뒤로 이동하면서 새로운 알파벳이 나오면 cnt++ 해준다.
3. cnt가 N보다 작거나 같을 때 r - l의 길이를 최대값과 비교 갱신해준다.
4. 만약 cnt가 N보다 크면 cnt가 N이 될때까지 l를 오른쪽으로 땡겨준다.

```java
while(r < end) {
    r++;
    if(r == end)	break;
    // 새로운 종류의 알파벳이 나오면  cnt++
    if(alpha[s.charAt(r) - 'a']++ == 0) {
        cnt++;
    }
    // cnt가 N보다 작거나 같으면 길이 갱
    if(cnt <= N) {
        max = Math.max(r - l + 1, max);
    }else {			// 아니면 l을 오른쪽으로 땡겨오기 
        while(l < r && cnt > N) {
            if(alpha[s.charAt(l) - 'a']-- == 1)
                cnt--;
            l++;
        }
    }
}
```

### 정리
투포인터가 정확히 어떤건지 몰랐는데 이번 기회에 제대로 공부가 됐다. 슬라이딩 윈도우랑 비슷한 문제였던 것 같다.