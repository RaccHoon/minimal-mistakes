---
layout: single
title: "Mall Mania(4268)"
categories: Algorithm_문제풀이
tag: [Dev, Algorithm, Graph, BFS, C++]
author_profile: false
---

# Mall Mania

## 문제 유형/난이도
>골드 5 / BFS

## 문제
> <a href="https://www.acmicpc.net/problem/4268">문제 바로 가기(baekjoon 4268)</a>

## 코드
```c++
#include <iostream>
#include <queue>

using namespace std;

const int dx[4] = {1, 0, -1, 0};
const int dy[4] = {0, -1, 0, 1};

struct Pos {
    int y;
    int x;
    int moveDis;
};

int getDis(vector<Pos>& shop1, vector<vector<bool> >& target, vector<vector<bool> >& visited) {
    queue<Pos> q;

    for(int i=0; i<shop1.size(); i++) {
        Pos pos = {shop1[i].y, shop1[i].x, 0};

        q.push(pos);
    }

    int ret=0;

    while(!q.empty()) {
        Pos pos = q.front();
        q.pop();

        if(pos.x<0 || pos.x>1999 || pos.y<0 || pos.y>1999) continue;

        if(visited[pos.y][pos.x]) continue;
        visited[pos.y][pos.x] = true;

        if(target[pos.y][pos.x]) {
            ret = pos.moveDis;
            break;
        }

        for(int i=0; i<4; i++) {
            int nextX = pos.x+dx[i];
            int nextY = pos.y+dy[i];

            Pos nextPos = {nextY, nextX, pos.moveDis+1};
            q.push(nextPos);
        }
    }

    return ret;
}

int main() {
    while(true) {
        int spotNum1, spotNum2;
        cin>>spotNum1;

        if(spotNum1==0) break;

        vector<Pos> shop1(spotNum1);

        for(int i=0; i<spotNum1; i++) {
            cin>>shop1[i].y>>shop1[i].x;
        }

        cin>>spotNum2;
        vector<vector<bool> > target(2000, vector<bool>(2000, false));
        vector<vector<bool> > visited(2000, vector<bool>(2000, false));

        for(int i=0; i<spotNum2; i++) {
            int targetY, targetX;
            cin>>targetY>>targetX;

            target[targetY][targetX]=true;
        }

        cout<<getDis(shop1, target, visited)<<"\n";
    }
}
```

## 회고
문제 설명  
문제는 여러개의 테스트 케이스로 이루어져 있다. 한 테스트 케이스에선 두 개의 쇼핑몰이 주어진다. 각 쇼핑몰은 우선 쇼핑몰을 구성하는 정점의 개수 p가 먼저 주어지고, 이후 p개의 좌표 쌍이 주어진다. 예제에서 두번째 쇼핑몰은 정점이 여러 줄에 걸쳐서 주어지는데 딱히 신경 쓸 필요는 없다. 문제는 두 쇼핑몰 사이의 최단 거리를 구하는 것이고, 테스트 케이스 별로 한 줄에 답 한 개씩 출력하면 된다.  
두 쇼핑몰 중 한 쇼핑몰만 큐에 좌표를 저장하고, 다른 한 쇼핑몰은 이차원 bool형 벡터로 위치만 저장해 둔다. 이후 bfs를 통해 탐색을 하다 다른 쇼핑몰의 위치에 도착하면 앞서 정의한 bool형 배열에 의해 바로 판별할 수 있기 때문에 거리를 리턴하고 함수를 종료한다.   