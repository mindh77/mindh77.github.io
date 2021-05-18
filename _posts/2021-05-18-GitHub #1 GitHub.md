---
layout: single
categories:
 - GitHub
use_math: true
---

## GitHub Study \#1. GitHub



GitHub의 다양한 용어들에 대해서 알아봅니다.

#### Commit

커밋은 게임에서 세이브에 해당하는 행동이라고 볼 수 있습니다. 즉, 언제든지 우리는 커밋한 시점으로 돌아갈 수 있다는 뜻입니다. 커밋을 하려면 저장을 원하는 파일들을 묶어서 커밋 명령을 수행하면 됩니다.  

#### Add (Stage에 올림)

앞서 말한 저장을 원하는 파일들을 묶는 일을 스테이지에 파일을 올린다라고 표현합니다. 

#### GitHub에 업로드 (push)

커밋을 하면 현재 작업 내용의 세이브 데이터가 "내 컴퓨터"에 저장됩니다. 이걸 GitHub에 올림으로써 내 컴퓨터의 데이터가 날아가도 안전하게 다시 복구 할 수 있습니다.

즉, GitHub는 원격 저장소라고 볼 수 있습니다. 

#### 커밋 시 주의사항

1. 반드시 한 번에 하나의 논리적 작업만을 커밋합니다.
2. 커밋 메시지를 잘 적어야 합니다.

#### checkout

쉽게 마지막 커밋으로 돌아갈 수 있습니다.
코드뭉치 버리기 기능을 사용하면 변경사항을 되돌릴 수 있습니다.
코드뭉치 버리기 기능은 가장 마지막 깃허브에 올라간 내용과 다른 현재 로컬 파일에 대한 내용을 모두 변경해 줍니다. 

#### branch

기능 변경을 하고 싶을 때 생성 및 사용
즉, 어느 커밋 시점 이후에 브랜치를 생성하게 되면, 기존의 마스터 내용은 그대로 두고 새로운 내용을 새롭게 만든 브랜치 내에서 작업할 수 있게 된다.

#### merge

하나의 브랜치를 현재 브랜치와 합치는 것을 병합이라고 합니다.

##### fast forward merge

현재 master 브랜치가 commit1 (c1)에 있고, 작업 중인 version 2 브랜치가 commit4 (c4)에 있을 때,
이 둘을 병합하게 되면 master 브랜치가 c4까지 오게 되는 상황을 나타냅니다.

##### 두 개 이상의 브랜치를 병합

현재 master 브랜치가 commit1 (c1)에 있고, c1으로부터 version 2 브랜치와 version 3 브랜치가 생성되어 각각 c4, c6에 있다고 하자.
먼저 master 브랜치를 version 3 브랜치와 병합하고 나서, 다시 master 브랜치를 version 2와 병합하려고 한다면, 새로운 커밋 c7을 만들어 내게 됩니다.
새로운 커밋 c7를 만드는 과정에서 version 2와 version 3 사이에 충돌이 발생할 수 있는데 이는 직접 수동으로 해결해 주어야 합니다.





##### 참고 문헌

[참고영상1](https://www.youtube.com/watch?v=8AtHcXnJSdA&t=42s)
[참고영상2](https://www.youtube.com/watch?v=aBSKvrRzfw0)
[참고영상3](https://www.youtube.com/watch?v=xaV0xqs6epM)
[참고영상4](https://www.youtube.com/watch?v=teW1KmqHb9I)
