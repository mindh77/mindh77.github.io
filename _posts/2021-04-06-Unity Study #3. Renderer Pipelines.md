---
layout: single
categories:
 - Unity
---



## Unity Study \#3. Render Pipelines



Render pipeline은  Scene에 있는 콘텐츠들을 화면에 표시해주기 위한 일련의 과정을 의미합니다.

유니티에서는 다양한 render pipelines을 제공하고 있으며, 파이프라인마다 할 수 있는 능력, 성능이 다르기 때문에 어플리케이션(게임, 플랫폼)의 종류에 따라 적절한 파이프라인을 활용해야 합니다.

높은 수준에서 보면, render pipeline은 
Culling (카메라에서 보이지 않는 부분을 제거), 
Rendering (씬 파일로부터 영상을 만들어냄), Post-processing과 같은 작업으로 구성되어 있습니다.

프로젝트 생성 시 한 번 정해진 render pipeline은 개발 과정 중간에 바꾸기는 어려운데, 각 render pipeline마다  생성해내는 output이 다르고 각각 사용하는 특성들이 다르기 때문입니다.  

대표적으로 유니티에서 제공하는 파이프라인에 대해서 알아보겠습니다.

#### Built-in Render Pipeline

유니티의 가장 기본적인 render pipeline으로 general-purpose로 사용가능하지만, 커스터마이징에 제한이 있습니다. 

이 render pipeline에는 다양한 rendering path(Lighting과 Shading에 관련된 작업 방식)가 존재합니다.

1. Forward Rendering (Default)
   범용 목적 
   이 rendering path에서는 모든 버텍스와 오브젝트마다 빛을 계산하기 때문에 실시간으로 빛을 계산하는데 큰 비용이 듭니다.  따라서 적은 양의 real-time light를 사용하거나 lighting이 중요하지 않은 프로젝트에 적합한 방법입니다. 
2. Deferred Shading
   조명과 그림자를 가장 많이 고려하는 rendering path
   GPU 지원이 필요하기 때문에 타겟 하드웨어에서 이를 지원하는지를 고려해야 합니다. 따라서, real-time light가 많은 프로젝트나 lighting이 중요한 프로젝트에 적합한 방법입니다. 이러한 이점으로 인해 몇 가지 trade-off 사항들을 가지고 있기도 합니다. 
3. Legacy Deferred
   Deffered Shading과 비슷한 방법이지만, trade-off 항목들이 조금 다릅니다. 

#### Universial Render Pipeline (URP)

URP는 Scriptable Render Pipeline (SRP: C# script를 통해 랜더링을 조절할 수 있음)으로 빠르고 쉽게 커스터마이징이 가능합니다. 이를 기반으로 다양한 플랫폼(모바일, PC 등)에서 적절하게 최적화 된 그래픽을 제공할 수 있습니다.

#### High Definition Render Pipeline (HDRP)

HDRP 또한 SRP로 주로 트리플 A 퀄리티의 게임, 자동차 데모, 건축쪽 어플리케이션과 같이 고품질의 그래픽을 요구하는 프로젝트에서 사용할 수 있습니다. HDRP는 물리 기반 lighting과 material을 사용하며 forward와 deferred 랜더링을 모두 지원합니다. (GPU 필요) 



유니티 매뉴얼에서는 좀 더 자세한 설명이 되어 있지 않아, OpenGL의 rendering pipeline에 대해서 좀 더 알아보겠습니다. 

![RenderingPipeline](https://user-images.githubusercontent.com/28036481/113686344-1ef47c80-9702-11eb-8499-c9b62e6f429f.png){: .align-center}

위의 과정을 좀 더 자세하게 설명하면,

1. 먼저 vertex array object를 잘 정의합니다. (ex. 정육면체의 6개의 vertex)(Vertex Specification)
2. Vertex shader는 vertex의 속성들을 받아 사용자가 정의한 프로그램에 따라 output vertex를 내보냅니다. (ex. final position of the vertex)
3. Primitive Assembly는 최종적으로 계산된 vertex를 기반으로 정의된 코드에 따라 그룹으로 묶는 작업을 합니다. (ex. 삼각형을 만들라고 하면 세 개의 버텍스를 이용해 삼각형을 그림)
   추가로, Geometry Shader라는 쉐이더가 있는데 이는 주어진 vertex를 이용해 새로운 vertex를 만들어 내는 작업을 합니다. (ex. 삼각형을 분할해 삼각형 두개로 만들 수 있음)
4. Rasterization은 조립된 primitive를 해당하는 픽셀들로 맵핑하는 과정을 거칩니다. (ex. 삼각형이 점유해야 하는 픽셀들은 어떤 것들인지?)
5. Fragment Shader는 light, shadow등을 고려해 최종적으로 픽셀의 색을 결정해주는 역할을 합니다. 또한, 깊이 값을 확인하여 해당 fragment가 다른 오브젝트의 앞이나 뒤에 있는지 확인하게 됩니다. (alpha value 값도 체크합니다.)



랜더링 파이프라인은 결국 화면에 내가 만든것들을 어떻게 표현해줄 것인지를 해결하는 과정이고, 개발 플랫폼에 따라 다양한 방법이 존재한다는 것을 알 수 있겠습니다.



##### 참고 문헌

[유니티 메뉴얼(Render Pipelines)](https://docs.unity3d.com/Manual/render-pipelines-overview.html)

[위키백과(렌더링)](https://ko.wikipedia.org/wiki/%EB%A0%8C%EB%8D%94%EB%A7%81)

[OpenGL랜더링](https://www.khronos.org/opengl/wiki/Rendering_Pipeline_Overview)

