# 문제 정의

1. 5x5 25명의 학생 중 7명의 소문난 칠공주파를 결성하려 한다.
2. 7명은 서로 가로나 세로로 반드시 인접해 있어야 한다.
3. 7명 중 'S'의 수가 반드시 4명 이상이어야 한다.
4. 소문난 칠공주를 결성할 수 있는 모든 경우의 수를 구하시오

# 문제 풀이

1. 25명이 고정이므로 25 중 7명을 뽑는다(조합). selected[25]에 뽑았는지 아닌지를 체크
2. 7명을 뽑으면 이 7명 중 4명 이상이 S인지 확인한다. 좌표는 r = i/5,  c =i%5로 구함
3. 4명 이상이면 bfs로 첫 좌표를 큐에 넣고 사방탐색을 하면서 7명이 전부 인접한지 탐색

# 정리

조합을 이용한다는 생각과 일차원을 이차원 좌표롤 바꾸는 아이디어를 떠올리기 쉽지 않았다.