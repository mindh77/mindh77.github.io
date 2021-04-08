---
layout: single
categories:
 - Unity
---

## Unity Study \#4. Quaternion



유니티는 모든 회전을 표현하기 위해 Quaternion이라는 개념을 사용합니다.

우리가 일반적으로 알고 있는 각도를 표현하는 방식으로 Euler Angles (오일러 각)이 있다.

#### Euler Angle

오일러 각은 3차원 상의 물체가 놓인 방향을 표시하기 위한 각도입니다. 

![250px-Orientation_coordonnees_spheriques_generalisees](https://user-images.githubusercontent.com/28036481/113983976-8b4bb900-9885-11eb-98ab-4de0f7100450.png)

위의 그림과 같이 어떠한 물체의 방향을 <u>3차원 공간 좌표계의 회전</u>으로 표현하는 것입니다. 즉, z축을 기준으로 x-y좌표축이 얼마만큼 회전했는지, 회전된 x축을 기준으로 회전된 z-y 좌표축이 얼마만큼 회전했는지, 회전된 z축을 기준으로 회전된 x-y 좌표축이 얼마만큼 회전했는지를 표현해주는 것이라고 볼 수 있습니다.

그러나 오일러 각은 계산하는데 비용이 크게 들고, 짐벌 락이라는 한계가 있게 됩니다. 짐벌 락은 먼저 회전한 축이 아직 회전하지 않은 축까지 함께 회전시켜 발생하는 문제로 두 번째로 회전을 시킬 때 다른 회전 축들끼리 겹치는 현상을 의미합니다. 그렇게 겹치게 되면 해당 값으로 표현할 수 있는 자유도가 한 단계 하락하게 되는 문제가 발생하고, 실제로 이러한 문제로 인해 아폴로 11호의 자세를 제어하는데 문제가 발생했다고 합니다.

#### Quaternion

쿼터니언은 오일러와 다르게 순서대로 회전 축을 계산하지 않고, 한 번에 회전을 계산할 수 있도록 설계된 방법입니다. 

쿼터니언은 (x,y,z,w) 네 가지의 요소로 이루어져 있고, (x,y,z)는 벡터 w는 스칼라를 의미합니다. 이 사원수를 이용해서 회전 정보를 표현할 수 있습니다.

 어떠한 회전축(u)를 기준으로 쎄타만큼 회전하기위한 쿼터니언은 다음과 같이 만들 수 있습니다.
$$
\hat {q} = (cos{\frac{\theta}{2}}, sin{\frac{\theta}{2}}u),		|u|=1
$$
위와 같은 쿼터니언을 활용해서 특정 점(p)를 아래와 같이 회전시킬 수 있습니다. 
$$
\mbox{p} = (x,y,z) \\
p = (0, \mbox{p})\\
q = (cos{\frac{\theta}{2}}, sin{\frac{\theta}{2}}u)\\
p' = qpq^* ( * 켤레 복소수)
$$
위의 식을 통해 점 p는 새로운 점 p'로 회전된 상태가 됩니다. 

쿼터니언은 직관적으로 이해하기가 매우 어렵습니다. 따라서 유니티에서는 이를 쉽게 사용하기 위해 다양한 함수를 제공하고 있고, 쿼터니언 자체의 값을 수정하는 것을 허용하고 있지 않습니다. 

대표적으로 Quaternion.LookRotation, Angle, Euler, Slerp, FromToRotation, identity 함수를 많이 사용한다고 합니다.

1. LookRotation
   주어진 up 벡터로부터 forward 벡터의 쿼터니언을 구합니다.

2. Angle
   두 rotation a와b 사이의 각도를 반환합니다.

3. Euler
   Euler 값을 쿼터니언으로 변환합니다.

4. Slerp
   From 쿼터니언과 to 쿼터니언 사이를 보간합니다.

5. FromToRotation
   From 쿼터니언에서 to 쿼터니언으로 회전할 rotation 쿼터니언 값을 반환합니다.

6. identity

   회전 없음을 나타내는 쿼터니언입니다.



특히, Slerp는 일반적인 Lerp와 다른 점이 있습니다. 

![Slerp](https://user-images.githubusercontent.com/28036481/113990966-f6e55480-988c-11eb-815f-726bd25cc9df.PNG)

일반적으로 interpolation을 할 때 Lerp를 사용하게 되면, 위처럼 회전을 표현하는 원 위에 점이 표현되는 것이 아니라 점과 점 사이의 직선 중간을 표현하게 됩니다. Slerp는 이에 반해 회전을 표현하는 원 위에 보간되는 것을 보장해줍니다.

쿼터니언 개념은 매우 어렵지만, 유니티에서는 이를 잘 활용할 수 있는 다양한 함수들을 제공해주고 있습니다. 이를 잘 활용해서 쓰다보면 쿼터니언도 점점 친숙해 질 수 있을 것이라고 생각합니다!



##### 참고 문헌

[Euler Angles](https://ko.wikipedia.org/wiki/%EC%98%A4%EC%9D%BC%EB%9F%AC_%EA%B0%81)

[Euler Angles 설명](https://m.blog.naver.com/PostView.nhn?blogId=dj3630&logNo=221447943453&proxyReferer=https:%2F%2Fwww.google.com%2F)

[Quaternion 설명](https://www.youtube.com/watch?v=_nJLDmue0h4)

[ Quaternion](https://docs.unity3d.com/kr/530/ScriptReference/Quaternion.html)

