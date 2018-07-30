---
title: "LINQ 집합작업"
date: 2018-07-28 16:40
categories: linq
---

### Distinct
중복 값 제거

```cs
var listA = new List<int>() {1,2,2,3,4,3};
var result = listA.Distinct ();
foreach (var a in result)
{
    Console.Write(a + ",");
}
```

결과
```cs
1,2,3,4,
```


### Except
두 컬렉션의 차집합

```cs
var listA = new List<int>() {1,2,3,5};
var listB = new List<int>() {1,3,4,5};
var result = listA.Except(listB);
foreach (var a in result)
{
    Console.Write(a + ",");
}
```

결과
```cs
2,
```


### Intersect
두 컬렉션의 교집합

```cs
var listA = new List<int>() {1,2,3,5};
var listB = new List<int>() {1,3,4,5};
var result = listA.Intersect(listB);
foreach (var a in result)
{
    Console.Write(a + ",");
}
```

결과
```cs
1,3,5,
```

### Union
두 컬렉션의 합집합

```cs
var listA = new List<int>() {1,2,3,5};
var listB = new List<int>() {1,3,4,5};
var result = listA.Union(listB);
foreach (var a in result)
{
    Console.Write(a + ",");
}
```

결과
```cs
1,2,3,4,5,
```