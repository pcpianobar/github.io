---
title: "LINQ 데이터 필터링"
date: 2018-07-28 16:43
categories: linq
---
### Where
조건자 함수를 기반으로 하는 값을 선택한다.

```cs
string[] words = {"the", "quick", "brown", "fox", "jumps"};
IEnumerable<string> query = from word in words
							where word.Length == 3
							select word;
// 위와 동일
// var query = words.Where(x => x.Length == 3);

foreach (var str in query)
	Console.WriteLine(str);

/* output :
	the
	fox
*/
```

### OfType
지정된 형식으로 캐스트할 수 있는지 여부에 따라 값을 선택한다.

```cs
List<Item> items = new List<Item>();
items.Add(new Sword() { Name = "단검"});
items.Add(new Sword() { Name = "장검"});
items.Add(new Shield() { Name = "강철 방패"});

var query = items.OfType<Shield>();

foreach (var item in query)
	Console.WriteLine(item.Name);

/* output :
	강철 방패
*/
```
