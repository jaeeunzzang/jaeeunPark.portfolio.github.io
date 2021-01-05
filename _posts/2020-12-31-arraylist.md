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

    public void expandSize() { //배열 크기 넘어가면 자동으로 크기 늘려준당..
		if (size >= elementData.length) {
			Object[] elementData2 = new Object[size * 2];
			for (int i = 0; i < elementData.length; i++) {
				elementData2[i] = elementData[i];
			}
			this.elementData=elementData2;
		}

	}
    public boolean addLast(Object element){ //끝에 데이터 추가
        elementData[size] = element; //elementData[0]=10
        size++;
        expandSize();
        return true;
    }
    public boolean add(int index,Object element){ //중간에 데이터 추가
        for(int i=size-1;i>=index;i--){
        elementData[i+1]=elementData[i]; //elementData[3]=elementData[2]
        }
        elementData[index]=element;
        size++;
        expandSize();
        return true;
    }
    public boolean addFirst(Object element){ //첫번째에 데이터 추가
        return add(0,element);
    }
    public Object get(int index){ //데이터 조회
        return elementData[index];
    }
    public String toString(){
        String str="[";
        for(int i=0;i<size;i++){
            str+=elementData[i];
            if(i<size-1){//size가 3이라면... i가 2일 때 까지만 쉼표를 붙인다.
            str+=",";
            }
        }
        return str+"]";
    }
    public int size(){ //배열 크기 반환
        return size;
    }
    public int indexOf(Object element){ //검색
        for(int i=0;i<size;i++){
            if(element.equals(elementData[i])){
                return i;
            }
        }
            return -1; //없으면 -1 반환
    }
    public boolean remove(int index){
	        elementData[index]="null";

	        for (int i=index;i<size;i++){
	            elementData[i]=elementData[i+1];
	        }
	        size--;
	        return true;
	    }

	public boolean removeFirst() {
		return remove(0);
	}

	public boolean removeLast() {
		elementData[size - 1] = "null";
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
