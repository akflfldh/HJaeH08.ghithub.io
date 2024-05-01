---
title: "소켓 스트림방식,데이터그램방식"

categories: -Socket

toc: true
toc_sticky: true
layout: post
date: 2024-04-23
last_modified_at: 2024-04-23
---


# 트리의 Depth 알고리즘과 시간복잡도


# Tree에서 노드의 Depth정의:
루트 노드부터 시작해서 해당노드까지 가기위해 중간에 노드들을 거쳐간 횟수 ,또는 그 노드의 조상노드의 개수 
\
\
![트리Depth](https://github.com/akflfldh/akflfldh.github.io/assets/52809733/7aede286-3d00-4f1f-bb79-8df816dffa93)
\
\
\
\
# 트리에서 특정노드의 Depth를 구하는 알고리즘: 
Depth를 구할려는 노드가 주어졌다고 가정한다.
\
\
**방법1:비재귀적으로 생각하기**
\
Depth 값은 조상노드의 개수라고 하였으니 그 노드의 조상노드들을 Root노드까지 거슬러올라가면서 조상노드들의개수를 세면 그값이 Depth값이다. 
\
\
**의사코드:**
\
 &emsp;Node * 현재노드=Depth를 구하고자하는 노드
\
\
&emsp;카운트=0
\
&emsp;&emsp;while(현재노드!=루트노드){
\
&emsp;&emsp;&emsp;카운트++
\
&emsp;&emsp;&emsp;현재노드=현재노드의 부모노드
\
&emsp;&emsp;}
\
\
\
**방법2 : 재귀적으로 계산하기**
\
현재노드의 Depth는 부모노드의 Depth+1이므로 부모노드의 Depth를계산해서 1을 더하면된다.
\
\
그럼 부모노드는 자신의 부모노드의 Depth에 1을더해서 Depth를 계산한다.
\
\
이런식으로 루토노드까지 도달하게되고 루트노드의Depth는 0으로 정의되었으니 0을 리턴한다.
\
\
\
\
**의사코드:**
\
&emsp;Depth(현재노드){
\
&emsp;&emsp;if(현재노드==루트노드)
\
&emsp;&emsp;&emsp;return 0
\
&emsp;&emsp;else{
\
&emsp;&emsp;&emsp;return 1+Depth(현재노드의 부모노드);
\
&emsp;&emsp;}
\
}
\
\
\
\
\
# 재귀적 방식의 시간복잡도
한 노드에서 Depth함수를 수행하는데 걸리는 시간복잡도는 O(1) 상수시간(내부에서 호출한 부모노드에대한 Depth함수의 시간은 반영하지않음)
\
\
그 Depth함수를 수행하는 노드의총개수는 Depth를구하려는 노드와 그의 조상노드들이기에
\
시간복잡도는 O(1(Depth를구하려는 노드)+조상노드의개수)이다.