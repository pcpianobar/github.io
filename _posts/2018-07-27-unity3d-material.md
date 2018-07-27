---
title: "Unity3d에서 material vs sharedMaterial 차이"
date: 2018-07-27 11:47
categories: unity3d material sharedMaterial
---

### 메뉴얼
Unity3d의 메뉴엘에 아래와 같이 설명되어 있다.
```
Renderer.sharedMaterial

현재 오브젝트에서 공유되는 재질(material)을 나타냅니다.
sharedMaterial 에서 재질을 수정하면, 해당 재질을 사용하는 모든 오브젝트의 모습이 변하게 되고, 프로젝트에 저장되어 있는 재질의 설정도 변경시킵니다.
sharedMaterial에 의해 반환된 재질의 수정을 권장하지 않습니다. 렌더러의 재질을 수정하고 싶은 경우에 material를 대신 사용합니다.
```

### 덧붙임
기본적으로 랜더링될때 매터리얼은 sharedMaterial을 참조한다. 이는 Batch 렌더링을 위해서 이다. (동일한 재질들은 한번에 렌더링하기 때문)
해당 Renderer의 매터리얼만 수정을 하고 싶다면 material을 사용해야 한다. material를 사용하면 자동으로 sharedMaterial의 사본을 생성해 할당해 준다. (에디터 상에서 확인해 보면 이름에 Instance가 붙어 있다.)

sharedMaterial을 수정하면 원본 에셋파일을 수정하는것과 동일하다. 그리고 자동으로 저장까지 된다.

상황에 맞게 material이나 sharedMaterial 을 사용해야 한다.

### 일시적으로 재질 속성 변경하기
MaterialPropertyBlock 를 이용하면 된다.


## 참조
https://docs.unity3d.com/kr/530/ScriptReference/Renderer-sharedMaterial.html
http://cacodemon.tistory.com/entry/material-과-sharedMaterial-그리고-Material-Property-Block
