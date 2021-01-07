---
layout: post
title: "Data Structure - List - LinkedList"
date: 2021-1-1 17:33:00 +0900
categories: [algorithm, java, study]
---

### LinkedList

데이터의 추가/삭제가 빈번하다면 LinkedList가 효과적(연결되어있는 링크를 끊고 새로 링크를 연결)<br>

```java
class LinkedList {
	private Node head;
	private Node tail;
	private int size=0;

	static class Node {
		private Object data;
		private Node next;

		public Node(Object data) {
			this.data = data;
			this.next = null;
		}

		public String toString() {
			return String.valueOf(this.data);
		}
	}

	public void addFirst(Object data) {// 처음 위치에 추가
		Node newNode = new Node(data);

		newNode.next = head;
	//기존의 head Node는 새로운 Node의 Next Node로 밀리게 된다
		head = newNode;
	//새로운 Node를 head Node로 지정.

		size++; //리스트 크기 증가
		if (head.next == null) { //next노드가 없으면
			tail = head; //head를 tail로 지정
		}
	}
	public void addLast(Object data){ //마지막 위치에 추가
		Node newNode=new Node(data);
		if(size == 0){ //리스트에 처음 add하는거며는
            addFirst(data);
        }
        else {
            tail.next = newNode;
			//tail Node의 다음순서에 새로운 Node를 추가.
			//[기존노드][tail노드][새노드]
            tail = newNode;
			//tail노드를 새로운 노드로 변경
			//[기존][새노드][tail노드]
            size++;
        }
	}
	 public void add(int index,Object data){ //인덱스 위치에 추가

        if(index == 0){
            addFirst(data);
        }
        else{
            Node tmp_1 = Node(index-1);
            Node tmp_2 = tmp_1.next;
            Node newNode = new Node(data);

            tmp_1.next = newNode;
            newNode.next = tmp_2;
            size++;

            if(newNode.next == null){
                tail = newNode;
            }
        }
    }
	public Object remove(int idx){ //인덱스 위치 삭제
        if(idx == 0){
            return removeFirst();
        }
        Node tmp = Node(idx-1);
        Node willDelete = tmp.next;
        tmp.next = tmp.next.next;

        Object data = willDelete.data;
        if(willDelete == tail){
            tail = tmp;
        }
        willDelete = null;
        size--;

        return data;
    }
}

public class Vectorlist {
	public static void main(String[] args) {
		LinkedList ll = new LinkedList();
		ll.addFirst("java");

	}
}
```
