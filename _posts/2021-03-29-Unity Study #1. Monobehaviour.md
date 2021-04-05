---
layout: single
typora-copy-images-to: .\img
categories: Unity
---

## Unity Study \#1. Monobehaviour 클래스란 무엇일까?



Monobehaviour는 유니티에서 모든 클래스가 상속받는 클래스입니다.

Monobehaviour 클래스 자체도 Object, Component, Behaviour와 같은 클래스를 상속받아 만든 클래스입니다.

유니티의 오브젝트에 컴포넌트로 사용하기 위해서는 반드시 이 클래스를 상속받아야 합니다.

이 말은 반대로 Monobehaviour 클래스를 상속받은 클래스(A)가 오브젝트에 컴포넌트로 등록되어 있지 않다면,  (A) 클래스는 다른 클래스에서 그 자체적으로 사용할 수 없다는 뜻입니다.
또한, (A) 클래스는 new 연산자를 이용해 동적으로 생성할 수 없고, 항상 컴포넌트 형태로 존재해야 합니다.

Monobehaviour 컴포넌트를 포함한 오브젝트는 다음과 같은 생명주기를 가지게 됩니다.

![Monobehaviour lifecycle](https://user-images.githubusercontent.com/28036481/113532636-d7d59100-9606-11eb-9efc-4e9504004d1c.png)

유니티 프로그래밍을 할 때에는 위와 같은 생명주기 순서를 고려하여 적절히 설계해야 합니다.

예를 들어, 특정 캐릭터가 애니메이션에 의해 움직이고 있을 때, 스크립트 상에서 이 캐릭터 움직임에 변화를 주고 싶다면
Update 문이 아닌 LateUpdate문과 같이 "Internal animation update"적용 이후에서 변화를 주어야 합니다.

비슷하게 Update 문 안에서 특정한 GameObject의 위치를 옮긴다고 바로 옮겨지지 않고 다음 프레임의 Physics 파트에서 옮겨지게 됩니다.

