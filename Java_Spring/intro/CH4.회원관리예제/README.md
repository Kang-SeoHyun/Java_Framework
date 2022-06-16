# 🎅🏻CH4.회원 관리 예제🎅🏻

## 😋백엔드 개발 맛보기😋 
1. [비즈니스 요구사항 정리](#🎁-비지니스-요구사항-정리🎁)  
2. [회원 도메인과 리포지토리 만들기](#🎁-회원-도메인과-리포지토리-만들기🎁)  
3. [회원 리포지토리 테스트 케이스 작성](#🎁-회원-리포지토리-테스트-케이스-작성🎁)  
4. [회원 서비스 개발](#🎁-회원-서비스-개발🎁)  
5. [회원 서비스 테스트](#🎁-회원-서비스-테스트🎁)  


### 🎁 비지니스 요구사항 정리🎁

* 비즈니스 요구사항 정리  
    * 데이터: 회원ID, 이름  
    * 기능: 회원 등록, 조회  
        * 아직 데이터 저장소가 선정되지 않음  

* 일반적인 웹 애플리케이션 계층 구조  
    ![image](https://user-images.githubusercontent.com/77817094/173293312-aeea17a1-2bbc-4c53-8f8c-2b5e126a4af0.png)  
    * 컨트롤러: 웹 MVC의 컨트롤러 역할, API만들때도  
    * 서비스: 서비스 클래스에 핵심 비즈니스 로직이 구현되어 있음 
        * 비즈니스 도메인 객체를 가지고 그 로직을 구현하는 계층   
    * 리포지토리: 데이터베이스에 접근, 도메인 객체를 DB에 저장하고 관리  
    * 도메인: 비즈니스 도메인 객체  
        * 예) 회원, 주문, 쿠폰 등등 주로 데이터베이스에 저장하고 관리됨    

* 클래스 의존관계  
    ![image](https://user-images.githubusercontent.com/77817094/173294250-06909cc1-9cac-41fb-87ae-f8bd797d6872.png)  
    ```
    * 개발을 진행하기 위해서 초기 개발 단계에서는 구현체로 가벼운 메모리 기반의 데이터 저장소 사용  

    * 아직 데이터 저장소가 선정되지 않아서, 우선 인터페이스로 구현 클래스를 변경할 수 있도록 설계  
     -> 나중에 구체적인 기술이 선정이 되면 바꿔 끼울 수 있게 interface 정의함.  

    * 데이터 저장소는 RDB, NoSQL 등등 다양한 저장소를 고민중인 상황으로 가정
    ```
### 🎁 회원 도메인과 리포지토리 만들기🎁  

> 1. 회원 만들고  
> 3. 그 회원들 저장하는 repository 메모리 만들고  
> 2. 나중을 위해서 repository 인터페이스 만들고!  
> 끝‼


☝🏻. domain 패키지에 회원 class 생성 - 객체  
![image](https://user-images.githubusercontent.com/77817094/174017489-61440d1a-cf39-460a-9307-de951b85b753.png)  
    
```java
package hello.hellospring.domain;

public class Member {

    private Long id;
    //시스템이 정해주는거
    private String name;
    //회원이 로그인할때 적는거
    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}

```

✌🏻. 회원 repository interface 생성   
![image](https://user-images.githubusercontent.com/77817094/174018506-9ef55c43-0d0c-40e1-81bb-f69b67c0960a.png)  

```java
package hello.hellospring.repository;

import hello.hellospring.domain.Member;

import java.util.List;
import java.util.Optional;

public interface MemberRepository {
    Member save (Member member);
    //저장된 회원 반환
    Optional<Member> findById(Long id);
    //id로 회원찾는 기능
    //optional은 자바8에 들어간 기능 - id가 null인 경우를 위해
    Optional<Member> findByName(String name);
    //name으로 회원찾는 기능
    List<Member> findAll();
    //지금까지 저장한 모든 회원리스트를 반환해줌
}
```   

👌🏻. 회원 repository 메모리 생성(구현)   
![image](https://user-images.githubusercontent.com/77817094/174019234-5196ed8c-eef3-4283-ab4f-4c2d3df9c708.png)   
```java
package hello.hellospring.repository;

import hello.hellospring.domain.Member;

import java.util.*;

//뒤에 implements MemberRepository 쓰고 Alt+Enter 누르면
//implement method 할 수 있음. (뒤에 override) 재네 생김.
public class MemoryMemberRepository implements MemberRepository {

    private static Map<Long, Member> store = new HashMap<>();
    //저장할 곳 = map
    //실무에서는 해쉬맵 동시성문제땜에 잘 안쓰긴 함.
    private static long sequence = 0L;
    //시퀀스는 0,1,2이런식으로 키값 저장해주는 애라고 보면됨

    @Override
    public Member save(Member member) {
        member.setId(++sequence);
        //sequence 값 올려줘서 id 세팅해줌
        store.put(member.getId(), member);
        //스토어에 저장하면 map 에 저장됨.
        return member;
    }

    @Override
    public Optional<Member> findById(Long id) {
        return Optional.ofNullable(store.get(id));
        //원래 store.get(id)인데, null 이 반환될 가능성이 있어서
        // Optional.ofNullable()로 감싸줌.
    }

    @Override
    public Optional<Member> findByName(String name) {
        return store.values().stream()
                .filter(member -> member.getName().equals(name))
                .findAny();
        //findAny()의 결과가 optional 로 반환됨.
        //맵에서 돌면서 이름 값은애 찾고 못찾으면 널값이 포함되면서 반환
    }

    @Override
    public List<Member> findAll() {
        return new ArrayList<>(store.values());
        //스토어에 있는 멤버들을 반환함.
    }
}
```   

### 🎁 회원 리포지토리 테스트 케이스 작성🎁  

### 🎁 회원 서비스 개발🎁

### 🎁 회원 서비스 테스트🎁
