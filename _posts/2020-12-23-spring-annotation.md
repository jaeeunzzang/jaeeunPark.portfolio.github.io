---
layout: post
title: "Spring @Annotation - Autowired, Resource ,Inject"
date: 2020-12-23 11:56:00 +0900
categories: [spring, study]
---

### 어노테이션이란?

@를 이용한 주석이다. 자바 코드에 주석을 달아 특별한 의미를 부여한 것

우리가 본 가장 첫 어노테이션은 @override

클래스, 메소드,변수 등 모든 요소에 선언이 가능하다.

메타데이터(실제데이터가 아닌 Data를 위한 데이터) 라고도 불리고 JDK5부터 등장.

**컴파일러가 특정 오류를 억제하도록 지시하는 것과 같이 프로그램 코드의 일부가 아닌**

**프로그램에 관한 데이터를 제공, 코드에 정보를 추가하는 정형화된 방법**

AOP(Aspect Oriented Programing; 관심지향프로그래밍)을 편리하게 구성할 수 있다.

### 왜? 사용하는 걸까

데이터에 대한 유효성 검사 조건을 어노테이션을 사용하여 Model 클래스에 직접 명시함으로써

해당 **데이터들에 대한 유효 조건을 쉽게 파악할 수 있게 되며, 코드의 양도 줄어든다.**

코드도 깔끔해지고 어노테이션의 재사용도 가능해진다.

### 특징

- 컴파일러에게 코드 문법 에러를 체크하도록 정보를 제공한다.
- 소프트웨어 개발툴이 빌드나 배치 시 코드를 자동으로 생성할 수 있도록 정보를 제공한다.
- 어노테이션을 만들 때 용도를 분명하게 해야 한다.
  - 소스상에서만 유지해야 할지
  - 컴파일된 클래스에도 유지해야 할지
  - 런타임 시에도 유지해야 할지를 지정해야 한다.
    <br>

## annotation목록

- Bean 의존 관계 주입시 사용 Annotation

  - @Autowired : 주입하려고 하는 **객체의 타입이 일치**하는 객체를 자동으로 주입<br>
    필드(멤버변수), 생성자, setter에 붙일 수 있다.

        > 타입→이름→@Qualifier 순서로 찾는다

  - @Inject : 주입하려고 하는 **객체의 타입이 일치**하는 객체를 자동으로 주입한다.<br>
    필드(멤버변수), 생성자, setter,멤버변수에 붙일 수 있다.

        > 타입→@Qualifier→이름 순서로 찾는다

  - @Resource : 주입하려고 하는 **객체의 이름(id)이 일치**하는 객체를 자동으로 주입<br>
    필드(멤버변수), setter에 사용 가능.

        > 이름→타입→@Qualifier 순서로 찾는다

  - 만약 동일한 타입을 가진 bean 객체가 두 개 이상 있다면 스프링이 어떤 빈을 주입해야 할 지 알 수 없어서 스프링 컨테이너를 초기화하는 과정에서 Exception을 발생시킨다.<br>
    @Qualifier : 사용할 의존 객체를 선택할 수 있도록 해준다.

  ```jsx
  1. 설정에서 bean의 한정자 값을 설정한다.
  2. @Autowired 어노테이션이 적용된 주입 대상에 @Qualifier 어노테이션을 설정한다.
  3. 이때 @Qualifier의 값으로 앞서 설정한 한정자를 사용한다.

  /* bean */
  <context:annotation-config>
      <bean id="member1" class="example.Member">
          <qualifier value="m1"/>
      </bean>

      <bean id="member2" class="example.Member"/>
          <qualifier value="m2"/>
      </bean>
  <context:annotation-config/>

  /* java */
  pubic class MemberDao{
      @Autowired  @Qualifier("m1")
      private Member member;

      public void setMember(Member member){
          this.member = member;
      }
  }
  ```
