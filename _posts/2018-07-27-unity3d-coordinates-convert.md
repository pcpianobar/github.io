---
title: "3d 공간 좌표계에서 UI 공간 좌표계로 위치 변경"
date: 2018-07-27 13:00
categories: unity3d
---

### 순서
- 3d, ui 공간 좌표계를 렌더링 중인 각각의 카메라 구하기
- 두 카메라의 위치 차이 구하기
- ui 공간으로 변환할 3d 공간 좌표계의 위치값 구하기
- 변환할 위치값을 3d 공간 좌표계에서 스크린 공간 좌표계로 변환
- 스크린 좌표계로 변경된 값에 두 카메라의 위치값 차이를 감하기
- 사용될 ui 객체의 부모 RectTransform 구하기
- RectTransformUtility.ScreenPointToLocalPointInRectangle () 를 이용해서 스크린 좌표계의 위치값해 해당되는 ui 좌표계의 위치값을 얻기


```csharp
Camera camera3d; // 3d 좌표계를 렌더링하는 카메라
RectTransform destTransform; // ui 좌표계 변환에 사용될 대상 ui 객체
Vector3 targetPos; // 변환될 원본 위치
ParticleSystem effect; // 3d 공간의 위치값에 대응하는 ui 공간에 위치에 표시될 이펙트
var cameraUi = destTransform.GetComponentInParent<Canvas> ().worldCamera; // ui 카메라
var distPos = _targetCamera.transform.position - uiCamera.transform.position; // 두 공간의 위치 차이
var screenPos = targetPos - distPos;  

var parentRect = destTransform.parent as RectTransform;
var localPos = Vector2.zero; // 3d 공간 좌표계에 해당되는 ui 좌표계의 위치값이 저장될 변수
RectTransformUtility.ScreenPointToLocalPointInRectangle (parentRect, screenPos, uiCamera, out localPos);

effect.transform.SetParent (parentRect);
effect.transform.localPosition = localPos;
effect.Play ();
```
