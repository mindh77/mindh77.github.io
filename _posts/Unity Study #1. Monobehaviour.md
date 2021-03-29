---
layout: single
typora-copy-images-to: .\img
---



## Unity Study \#1. Monobehaviour 클래스란 무엇일까?



Monobehaviour는 유니티에서 모든 클래스가 상속받는 클래스입니다.

Monobehaviour 클래스 자체도 Object, Component, Behaviour와 같은 클래스를 상속받아 만든 클래스입니다.



유니티의 오브젝트에 컴포넌트로 사용하기 위해서는 반드시 이 클래스를 상속받아야 합니다.

이 말은 반대로 Monobehaviour 클래스를 상속받은 클래스(A)가 오브젝트에 컴포넌트로 등록되어 있지 않다면,  (A) 클래스는 다른 클래스에서 그 자체적으로 사용할 수 없다는 뜻입니다.

또한, new 연산자를 이용해 동적으로 생성할 수 없고 항상 컴포넌트 형태로 존재하게 됩니다.



Monobehaviour 컴포넌트를 포함한 오브젝트는 다음과 같은 생명주기를 가지게 됩니다.

![Monobehaviour lifecycle](D:\GIthub Blog\img\Monobehaviour lifecycle.png)

