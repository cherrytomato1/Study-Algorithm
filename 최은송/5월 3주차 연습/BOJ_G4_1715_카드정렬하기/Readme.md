# 문제 정의

1. 정렬된 두 묶음의 숫자 카드 A, B를 하나로 만드는 데 A+B번의 비교를 해야 한다.
2. 10, 20, 40이 있으면 (10+20) + (30 + 40) = 100번의 비교가 가장 효율적인 방법이다.
3. N개의 숫자 카드 묶음의 주어질 때 최소 비교 횟수를 출력하시오

# 문제 풀이

1. 무조건 작은 숫자들부터 더해가면 최소값이 나온다.
2. PriorityQueue에 입력값을 넣어 오름차순으로 정렬해준다.
3. 만약 카드가 1개면 비교하지 않으니 0을 출력한다.
4. 아닐 경우: pq에서 두 카드를 빼고 더한 값을 결과값에 더해준다. 두 카드의 sum을 다시 pq에 넣어준다.
5. pq가 빌때까지 반복한다. 마지막 카드까지 더하면 sum은 pq에 넣을 필요가 없으니 조건문은 pq.size() > 1로 해준다.

# 정리

pq를 이용한 문제. 쉬웠다!