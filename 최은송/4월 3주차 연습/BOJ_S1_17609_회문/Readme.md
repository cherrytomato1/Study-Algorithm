# 문제정의

1. 회문: 앞뒤가 똑같은 단어
2. 유사회문: 한 문자를 삭제해서 회문으로 만들 수 있는 문자열
3. 문자열의 길이는 3 이상 100,000 이하이고 각 문자열마다 회문, 유사회문, 아닌 경우를 0,1,2로 출력하라

# 문제 풀이

1. i는 문자열 시작, j는 문자열 끝을 가리키는 투포인터롤 한칸씩 줄여가며 같은지 비교
2. 만약 i <  j인 경우까지 같다면 회문이니 return 0을 하면 된다
3. 만약 문자가 다르다면 유사회문인지 아닌지 판단해야 한다. 여기서 i+1 == j, i == j-1을 할 경우 반례에 걸린다. baaba인 경우 첫번째 문자를 삭제하는 경우와 마지막 문자를 삭제하는 경우 둘 다 문자가 같다. 그렇기 때문에 문자가 다른 인덱스부터 다시 팰린드롬 체크를 해줘야 한다.
    1. 만약 두번째 팰린드롬 체크에서도 다른 문자가 있으면 2 출력
    2. 두번째 팰린드롬 체크에서 i<j일때까지 문자가 같으면 유사 펠린드롬이므로 1 출력

# 정리

dfs로 풀었는데 시간초과가 난다?? 음 당연하군..왜냐면 문자열 길이가 십만개니까 같으면 넘기고 다를때만 재귀호출을 해야 한다.