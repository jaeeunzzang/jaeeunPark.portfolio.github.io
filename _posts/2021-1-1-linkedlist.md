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
	private int size;

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
//새로운 Node 들이 head Node로 지정해 주어야 한다. 기존의 head Node는 새로운 Node의 Next Node로 밀리게 된다
		newNode.next = head;
		head = newNode;

		size++;
		if (head.next == null) {
			tail = head;
		}
	}
}

public class Vectorlist {
	public static void main(String[] args) {
		LinkedList ll = new LinkedList();
		ll.addFirst("java");

	}
}
```
