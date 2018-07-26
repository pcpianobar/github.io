---
title: "LINQ 정렬하기"
date: 2018-07-27 11:47
categories: linq
---

## LINQ 정렬하기

### 참고
<https://docs.microsoft.com/ko-kr/dotnet/csharp/programming-guide/concepts/linq/sorting-data>
<https://m.blog.naver.com/PostView.nhn?blogId=empty_wagon&logNo=20148168775&proxyReferer=https%3A%2F%2Fwww.google.com%2F>

### 메서드
메서드 이름 | 설명 | C# 쿼리 식 구문 | 추가 정보
--- | --- | --- | ---
OrderBy  |  값을 오름차순으로 정렬합니다.  |  orderby  |  Enumerable.OrderBy, Queryable.OrderBy
OrderByDescending | 값을 내림차순으로 정렬합니다. | orderby … descending | Enumerable.OrderByDescending, Queryable.OrderByDescending
ThenBy | 2차 정렬을 오름차순으로 수행합니다. | orderby …, … | Enumerable.ThenBy, Queryable.ThenBy
ThenByDescending | 2차 정렬을 내림차순으로 수행합니다. | orderby …, … descending | Enumerable.ThenByDescending, Queryable.ThenByDescending
Reverse | 컬렉션에서 요소의 순서를 반대로 바꿉니다.	| 해당 사항 없음. | Enumerable.Reverse, Queryable.Reverse

### 오름차순(Ascending)
```csharp
var numbers = new List<int>() { 2, 3, 1, 7, 6, 9, 5, 8, 10, 4 };
var result = from n in numbers orderby n select n;
// 위와 동일
// var result = numbers.OrderBy(x => x);

foreach (int a in result)
{
    Console.Write(a + ",");
}
```

```
1,2,3,4,5,6,7,8,9,10,
```

### 내림차순(Descending)
```csharp
List<int> numbers = new List<int>() { 2, 3, 1, 7, 6, 9, 5, 8, 10, 4 };
var result = from n in numbers orderby n descending select n;
// 메서드구문
// var result = numbers.OrderByDescending (x => x);
foreach (int a in result)
{
    Console.Write(a + ",");
}
```

```
10,9,8,7,6,5,4,3,2,1,
```

### 여러 기준을 한 번에
```csharp
List<Item> items = new List<Item>();
items.Add(new Item() { Name = "컴퓨터", Type = "가전", Price = 1000000 });
items.Add(new Item() { Name = "모니터", Type = "가전", Price = 300000 });
items.Add(new Item() { Name = "냉장고", Type = "가전", Price = 700000 });
items.Add(new Item() { Name = "흠정역성경", Type = "책", Price = 20000 });
items.Add(new Item() { Name = "C언어 입문", Type = "책", Price = 35000 });
items.Add(new Item() { Name = "Visual Studio", Type = "소프트웨어", Price = 500000 });
 
var result = from i in items orderby i.Type, i.Price descending select i;
// 메서드 구분 
// var result = items.OrderBy(i => i.Type).ThenByDescending(i => i.Price).Select(i => i);
foreach (var i in result)
{
    Console.WriteLine(i.Name + " 가격 " + i.Price);
}
```

```
컴퓨터 가격 1000000
냉장고 가격 700000
모니터 가격 300000
Visual Studio 가격 500000
C언어 입문 가격 35000
흠정역성경 가격 20000
```

### 역순(Inverting)
```csharp
List<int> numbers = new List<int>() { 2, 3, 1, 7, 6, 9, 5, 8, 10, 4 };
var result = from n in numbers orderby n descending select n;
var reversed = result.Reverse();
 
foreach (int a in reversed)
{
    Console.Write(a + ",");
}
```

```
1,2,3,4,5,6,7,8,9,10,
```
