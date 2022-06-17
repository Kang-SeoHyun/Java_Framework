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
회원 repository 메모리 구현체 테스트
![image](https://user-images.githubusercontent.com/77817094/174022437-04a8622c-a1e1-4728-9eaf-e98f16685587.png)  

* 💦저장이 제대로 되는지 테스트💦
```java
package hello.hellospring.repository;

import hello.hellospring.domain.Member;
import org.junit.jupiter.api.Test;

public class MemoryMemberRepositoryTest {

    MemoryMemberRepository repository = new MemoryMemberRepository();

    @Test //2. 이걸 작성해줘야함.
    public void save(){
        //1. 이 기능이 동작하는지 보려면
        //3. 성공하면 초록불 뜸.
        Member member = new Member();
        member.setName("spring");

        repository.save(member);
        //멤버 저장하는거
        Member result = repository.findById(member.getId()).get();
        //제대로 들어갔나 검증하기 위해 result에 우선 저장.
        System.out.println("result = " + (result == member));
        //DB에서 꺼낸거랑 new로 만든거랑 똑같으면 성공!
    }

}
```    
* 실행 결과     
![image](https://user-images.githubusercontent.com/77817094/174022835-6544c566-5cf9-4613-9fe7-8e7a0fb0658c.png)   
-> 이렇게 나오는데 매번 출력 값을 볼 수는 없으니까 'assertions' 라는 기능이 있다.     

```java 
//System.out.println("result = " + (result == member));
Assertions.assertEquals(result,member);
```   
* 똑같을 경우.  
![image](https://user-images.githubusercontent.com/77817094/174023890-2ddd4c74-b2c1-4841-aab7-1eaf11af6228.png)  

* 다를 경우.  
![image](https://user-images.githubusercontent.com/77817094/174023983-cd2b9f42-ffe1-4f08-9bee-dac7454a7dc1.png)  

요새는 이 문법 많이 씀.  
```java
//System.out.println("result = " + (result == member));
//Assertions.assertEquals(result,null);
Assertions.assertThat(member).isEqualTo(result);
//요새는 이거 많이 씀
```  
Assertion뒤에서 옵션 열면 (alt + enter) static import 할 수 있음.  

```java
import static org.assertj.core.api.Assertions.*;
// 추가 되었으므로 
assertThat(member).isEqualTo(result);  
//로 쓸 수 있다.
```  

* 💦이름으로 찾아주는 테스트💦  
```java
@Test
public void findByName() {
    //멤버 두개 생성한 뒤
    Member member1 = new Member();
    member1.setName("spring1");
    repository.save(member1);

    Member member2 = new Member();
    member2.setName("spring2");
    repository.save(member2);

    //when
    Member result = repository.findByName("spring1").get();
    //then
    assertThat(result).isEqualTo(member1);
    //실행결과 = 참
    assertThat(result).isEqualTo(member2);
    //실행결과 = 거짓(안됨)
}
```

* 💦리스트 몇명인지 찾아주는 테스트💦  
```java  
@Test
public void findAll() {
    //멤버 두개 생성한 뒤
    Member member1 = new Member();
    member1.setName("spring1");
    repository.save(member1);

    Member member2 = new Member();
    member2.setName("spring2");
    repository.save(member2);

    //when
    List<Member> result = repository.findAll();
    //then
    assertThat(result.size()).isEqualTo(2);
    //실행결과 = 참
    assertThat(result.size()).isEqualTo(3);
    //실행결과 = 거짓(안됨)
    }
```

* ⁉ 문제 발생 ⁉  
![image](https://user-images.githubusercontent.com/77817094/174252231-d9336664-e87a-4d02-9caa-b6b1439282bd.png)  

    > 전체 테스트를 실행하기 위해서 class단위로 run을 하게되면 테스트들에 있는 객체가 이름이 같으면 (다른애 기준 먼저 정의된 애가 있으면) 실행오류가 뜬다. 따라서 test가 하나 끝날때마다 메모리를 리셋해줘야한다. = 리포지토리를 지워주는 코드 넣기.  

* 기능 위치  
![image](https://user-images.githubusercontent.com/77817094/174253843-7288a662-f0a7-4d82-9355-39e87a823dbd.png)  

```java  
@Override
public List<Member> findAll() {
    return new ArrayList<>(store.values());
    //스토어에 있는 멤버들을 반환함.
}

// 여기에 추가해주기
public void clearStore() {
    store.clear();
}
```
* 실행 위치  
![image](https://user-images.githubusercontent.com/77817094/174254443-2c08f426-8c1a-4a1b-89ee-f5fa6847bb79.png)  

```java

```
### 🎁 회원 서비스 개발🎁

### 🎁 회원 서비스 테스트🎁
