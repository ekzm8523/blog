---
title: "BST and Hash table"
date: 2022-06-19T12:33:13+09:00
categories:
- CS

tags:
- CS

aliases: [/post/cs/]
# keywords:
# - tech
#thumbnailImage: //example.com/image.jpg
---
<!--more-->

## BST는 어떤 자료구조인가요?
BST란 Binary Search Tree의 약자로 이진트리이기 때문에 당연히 child 노드는 최대 두개까지 가질 수 있습니다.
왼쪽 자식은 자신보다 작아야하고 오른쪽 자신은 자신보다 커야하는 규칙이 있습니다.
이렇게 구성했을때 search 시간복잡도는 O(log n)을 갖습니다.
하지만 최악의 경우 한쪽으로만 치우친 트리가 구성되어 worst case는 O(n)의 시간복잡도를 갖습니다.
이의 해결방안으로는 Red black Tree가 있습니다.

## Hash table은 어떤 자료구조 인가요?
파이썬에서 맨날 사용하는 dict 형태가 hash table이라고 볼 수 있습니다.
Hash table은 내부적으로 작동하는 원리까지 들어가면 알아야 할게 참 많은데 일단 key value 형태를 저장하는 자료구조입니다.
key값을 hash function에 넣어 나오는 index(메모리 주소)에 key, value를 저장합니다. 보통 hash function은 string형태도 index로 변환을 시켜주어야 하기 때문에 encoding방식은 구현에 따라 다르고 int로 변경된 뒤에 mod 연산을 통해 index로 변경해줍니다. (2012 mod 9 -> 5) 하지만 단순히 이런 방법으로는 같은 인덱스가 나올 수 있습니다. 그에 따른 후 처리를 해주어야 합니다.


## Hash table에서 collision이 발생하면 어떻게 되나요? 해결 방법엔 뭐가 있나요?
서로 다른 key값을 hash function에 넣어 인덱스를 뽑았을때 같은 인덱스가 나온경우 collision이 발생했다고 합니다.
해결방안에는 정말 여러가지가 있는데 일단 open addressing 방식은 다른 빈 인덱스를 찾아 나서는 방법입니다.
다른 빈 인덱스를 찾는 방법으로 한칸씩 이동하는 Linear Probing이 있고 제곱수만큼 이동하는 Quadratic Probing 방법이 있고 마지막으로 Double Hashing 방법이 있습니다.
Double Hashing방법은 앞서 말한 Linear나 Quadratic 방법은 인덱스가 몰린다는 단점이 존재해서 랜덤하게 인덱스를 탐색하기 위해서 Hash Functioin을 하나 더 태운거라고 볼 수 있습니다.

두번째로 separete chaining 방식이 있습니다.
이는 같은 인덱스에 도달하더라도 저장을 Linked list나 Tree구조로 저장하는 방법입니다.
Linked list형태로 저장한다면 같은 1 인덱스라도 여러 key value들을 저장할 수 있습니다.
하지만 최악의 경우는 인덱스 1에 계속 저장되어 search worst time이 O(n)까지 걸릴 수 있습니다.
