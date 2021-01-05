---
layout: post
title: "Data Structure - List - ArrayList"
date: 2020-12-31 14:47:00 +0900
categories: [algorithm, java, study]
---

### ArrayList 구현

내장되어있는 배열리스트는 동적으로 크기를 할당.<br>
지정된 크기 이상의 데이터가 들어오면 배열의 크기\*2 해주고 데이터를 복사해서 넣는다.

```java
public class ArrayList {
    private int size = 0;
    private Object[] elementData = new Object[100];
}
```

```java
public class Main {
    public static void main(String[] args) {
        ArrayList al = new ArrayList();
    }
```
