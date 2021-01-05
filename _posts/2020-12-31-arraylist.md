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

    public boolean addLast(Object element){
        elementData[size] = element; //elementData[0]=10
        size++;
        return true;
    }
    public boolean add(int index,Object element){
        for(int i=size-1;i>=index;i--){
        elementData[i+1]=elementData[i]; //elementData[3]=elementData[2]
        }
        elementData[index]=element;
        size++;
        return true;
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        ArrayList al = new ArrayList();
        al.addLast(10);
        al.addLast(20);
        al.addLast(30);
        al.add(1,15);
    }
```
