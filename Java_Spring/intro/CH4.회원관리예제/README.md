# ππ»CH4.νμ κ΄λ¦¬ μμ ππ»

## πλ°±μλ κ°λ° λ§λ³΄κΈ°π 
1. [λΉμ¦λμ€ μκ΅¬μ¬ν­ μ λ¦¬](#π-λΉμ§λμ€-μκ΅¬μ¬ν­-μ λ¦¬π)  
2. [νμ λλ©μΈκ³Ό λ¦¬ν¬μ§ν λ¦¬ λ§λ€κΈ°](#π-νμ-λλ©μΈκ³Ό-λ¦¬ν¬μ§ν λ¦¬-λ§λ€κΈ°π)  
3. [νμ λ¦¬ν¬μ§ν λ¦¬ νμ€νΈ μΌμ΄μ€ μμ±](#π-νμ-λ¦¬ν¬μ§ν λ¦¬-νμ€νΈ-μΌμ΄μ€-μμ±π)  
4. [νμ μλΉμ€ κ°λ°](#π-νμ-μλΉμ€-κ°λ°π)  
5. [νμ μλΉμ€ νμ€νΈ](#π-νμ-μλΉμ€-νμ€νΈπ)  


### π λΉμ§λμ€ μκ΅¬μ¬ν­ μ λ¦¬π

* λΉμ¦λμ€ μκ΅¬μ¬ν­ μ λ¦¬  
    * λ°μ΄ν°: νμID, μ΄λ¦  
    * κΈ°λ₯: νμ λ±λ‘, μ‘°ν  
        * μμ§ λ°μ΄ν° μ μ₯μκ° μ μ λμ§ μμ  

* μΌλ°μ μΈ μΉ μ νλ¦¬μΌμ΄μ κ³μΈ΅ κ΅¬μ‘°  
    ![image](https://user-images.githubusercontent.com/77817094/173293312-aeea17a1-2bbc-4c53-8f8c-2b5e126a4af0.png)  
    * μ»¨νΈλ‘€λ¬: μΉ MVCμ μ»¨νΈλ‘€λ¬ μ­ν , APIλ§λ€λλ  
    * μλΉμ€: μλΉμ€ ν΄λμ€μ ν΅μ¬ λΉμ¦λμ€ λ‘μ§μ΄ κ΅¬νλμ΄ μμ 
        * λΉμ¦λμ€ λλ©μΈ κ°μ²΄λ₯Ό κ°μ§κ³  κ·Έ λ‘μ§μ κ΅¬ννλ κ³μΈ΅   
    * λ¦¬ν¬μ§ν λ¦¬: λ°μ΄ν°λ² μ΄μ€μ μ κ·Ό, λλ©μΈ κ°μ²΄λ₯Ό DBμ μ μ₯νκ³  κ΄λ¦¬  
    * λλ©μΈ: λΉμ¦λμ€ λλ©μΈ κ°μ²΄  
        * μ) νμ, μ£Όλ¬Έ, μΏ ν° λ±λ± μ£Όλ‘ λ°μ΄ν°λ² μ΄μ€μ μ μ₯νκ³  κ΄λ¦¬λ¨    

* ν΄λμ€ μμ‘΄κ΄κ³  
    ![image](https://user-images.githubusercontent.com/77817094/173294250-06909cc1-9cac-41fb-87ae-f8bd797d6872.png)  
    ```
    * κ°λ°μ μ§ννκΈ° μν΄μ μ΄κΈ° κ°λ° λ¨κ³μμλ κ΅¬νμ²΄λ‘ κ°λ²Όμ΄ λ©λͺ¨λ¦¬ κΈ°λ°μ λ°μ΄ν° μ μ₯μ μ¬μ©  

    * μμ§ λ°μ΄ν° μ μ₯μκ° μ μ λμ§ μμμ, μ°μ  μΈν°νμ΄μ€λ‘ κ΅¬ν ν΄λμ€λ₯Ό λ³κ²½ν  μ μλλ‘ μ€κ³  
     -> λμ€μ κ΅¬μ²΄μ μΈ κΈ°μ μ΄ μ μ μ΄ λλ©΄ λ°κΏ λΌμΈ μ μκ² interface μ μν¨.  

    * λ°μ΄ν° μ μ₯μλ RDB, NoSQL λ±λ± λ€μν μ μ₯μλ₯Ό κ³ λ―Όμ€μΈ μν©μΌλ‘ κ°μ 
    ```
### π νμ λλ©μΈκ³Ό λ¦¬ν¬μ§ν λ¦¬ λ§λ€κΈ°π  

> 1. νμ λ§λ€κ³   
> 3. κ·Έ νμλ€ μ μ₯νλ repository λ©λͺ¨λ¦¬ λ§λ€κ³   
> 2. λμ€μ μν΄μ repository μΈν°νμ΄μ€ λ§λ€κ³ !  
> λβΌ


βπ». domain ν¨ν€μ§μ νμ class μμ± - κ°μ²΄  
![image](https://user-images.githubusercontent.com/77817094/174017489-61440d1a-cf39-460a-9307-de951b85b753.png)  
    
```java
package hello.hellospring.domain;

public class Member {

    private Long id;
    //μμ€νμ΄ μ ν΄μ£Όλκ±°
    private String name;
    //νμμ΄ λ‘κ·ΈμΈν λ μ λκ±°
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

βπ». νμ repository interface μμ±   
![image](https://user-images.githubusercontent.com/77817094/174018506-9ef55c43-0d0c-40e1-81bb-f69b67c0960a.png)  

```java
package hello.hellospring.repository;

import hello.hellospring.domain.Member;

import java.util.List;
import java.util.Optional;

public interface MemberRepository {
    Member save (Member member);
    //μ μ₯λ νμ λ°ν
    Optional<Member> findById(Long id);
    //idλ‘ νμμ°Ύλ κΈ°λ₯
    //optionalμ μλ°8μ λ€μ΄κ° κΈ°λ₯ - idκ° nullμΈ κ²½μ°λ₯Ό μν΄
    Optional<Member> findByName(String name);
    //nameμΌλ‘ νμμ°Ύλ κΈ°λ₯
    List<Member> findAll();
    //μ§κΈκΉμ§ μ μ₯ν λͺ¨λ  νμλ¦¬μ€νΈλ₯Ό λ°νν΄μ€
}
```   

ππ». νμ repository λ©λͺ¨λ¦¬ μμ±(κ΅¬ν)   
![image](https://user-images.githubusercontent.com/77817094/174019234-5196ed8c-eef3-4283-ab4f-4c2d3df9c708.png)   
```java
package hello.hellospring.repository;

import hello.hellospring.domain.Member;

import java.util.*;

//λ€μ implements MemberRepository μ°κ³  Alt+Enter λλ₯΄λ©΄
//implement method ν  μ μμ. (λ€μ override) μ¬λ€ μκΉ.
public class MemoryMemberRepository implements MemberRepository {

    private static Map<Long, Member> store = new HashMap<>();
    //μ μ₯ν  κ³³ = map
    //μ€λ¬΄μμλ ν΄μ¬λ§΅ λμμ±λ¬Έμ λμ μ μμ°κΈ΄ ν¨.
    private static long sequence = 0L;
    //μνμ€λ 0,1,2μ΄λ°μμΌλ‘ ν€κ° μ μ₯ν΄μ£Όλ μ λΌκ³  λ³΄λ©΄λ¨

    @Override
    public Member save(Member member) {
        member.setId(++sequence);
        //sequence κ° μ¬λ €μ€μ id μΈνν΄μ€
        store.put(member.getId(), member);
        //μ€ν μ΄μ μ μ₯νλ©΄ map μ μ μ₯λ¨.
        return member;
    }

    @Override
    public Optional<Member> findById(Long id) {
        return Optional.ofNullable(store.get(id));
        //μλ store.get(id)μΈλ°, null μ΄ λ°νλ  κ°λ₯μ±μ΄ μμ΄μ
        // Optional.ofNullable()λ‘ κ°μΈμ€.
    }

    @Override
    public Optional<Member> findByName(String name) {
        return store.values().stream()
                .filter(member -> member.getName().equals(name))
                .findAny();
        //findAny()μ κ²°κ³Όκ° optional λ‘ λ°νλ¨.
        //λ§΅μμ λλ©΄μ μ΄λ¦ κ°μμ  μ°Ύκ³  λͺ»μ°ΎμΌλ©΄ λκ°μ΄ ν¬ν¨λλ©΄μ λ°ν
    }

    @Override
    public List<Member> findAll() {
        return new ArrayList<>(store.values());
        //μ€ν μ΄μ μλ λ©€λ²λ€μ λ°νν¨.
    }
}
```   

### π νμ λ¦¬ν¬μ§ν λ¦¬ νμ€νΈ μΌμ΄μ€ μμ±π  
νμ repository λ©λͺ¨λ¦¬ κ΅¬νμ²΄ νμ€νΈ
![image](https://user-images.githubusercontent.com/77817094/174022437-04a8622c-a1e1-4728-9eaf-e98f16685587.png)  

* π¦μ μ₯μ΄ μ λλ‘ λλμ§ νμ€νΈπ¦
```java
package hello.hellospring.repository;

import hello.hellospring.domain.Member;
import org.junit.jupiter.api.Test;

public class MemoryMemberRepositoryTest {

    MemoryMemberRepository repository = new MemoryMemberRepository();

    @Test //2. μ΄κ±Έ μμ±ν΄μ€μΌν¨.
    public void save(){
        //1. μ΄ κΈ°λ₯μ΄ λμνλμ§ λ³΄λ €λ©΄
        //3. μ±κ³΅νλ©΄ μ΄λ‘λΆ λΈ.
        Member member = new Member();
        member.setName("spring");

        repository.save(member);
        //λ©€λ² μ μ₯νλκ±°
        Member result = repository.findById(member.getId()).get();
        //μ λλ‘ λ€μ΄κ°λ κ²μ¦νκΈ° μν΄ resultμ μ°μ  μ μ₯.
        System.out.println("result = " + (result == member));
        //DBμμ κΊΌλΈκ±°λ newλ‘ λ§λ κ±°λ λκ°μΌλ©΄ μ±κ³΅!
    }

}
```    
* μ€ν κ²°κ³Ό     
![image](https://user-images.githubusercontent.com/77817094/174022835-6544c566-5cf9-4613-9fe7-8e7a0fb0658c.png)   
-> μ΄λ κ² λμ€λλ° λ§€λ² μΆλ ₯ κ°μ λ³Ό μλ μμΌλκΉ 'assertions' λΌλ κΈ°λ₯μ΄ μλ€.     

```java 
//System.out.println("result = " + (result == member));
Assertions.assertEquals(result,member);
```   
* λκ°μ κ²½μ°.  
![image](https://user-images.githubusercontent.com/77817094/174023890-2ddd4c74-b2c1-4841-aab7-1eaf11af6228.png)  

* λ€λ₯Ό κ²½μ°.  
![image](https://user-images.githubusercontent.com/77817094/174023983-cd2b9f42-ffe1-4f08-9bee-dac7454a7dc1.png)  

μμλ μ΄ λ¬Έλ² λ§μ΄ μ.  
```java
//System.out.println("result = " + (result == member));
//Assertions.assertEquals(result,null);
Assertions.assertThat(member).isEqualTo(result);
//μμλ μ΄κ±° λ§μ΄ μ
```  
Assertionλ€μμ μ΅μ μ΄λ©΄ (alt + enter) static import ν  μ μμ.  

```java
import static org.assertj.core.api.Assertions.*;
// μΆκ° λμμΌλ―λ‘ 
assertThat(member).isEqualTo(result);  
//λ‘ μΈ μ μλ€.
```  

* π¦μ΄λ¦μΌλ‘ μ°Ύμμ£Όλ νμ€νΈπ¦  
```java
@Test
public void findByName() {
    //λ©€λ² λκ° μμ±ν λ€
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
    //μ€νκ²°κ³Ό = μ°Έ
    assertThat(result).isEqualTo(member2);
    //μ€νκ²°κ³Ό = κ±°μ§(μλ¨)
}
```

* π¦λ¦¬μ€νΈ λͺλͺμΈμ§ μ°Ύμμ£Όλ νμ€νΈπ¦  
```java  
@Test
public void findAll() {
    //λ©€λ² λκ° μμ±ν λ€
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
    //μ€νκ²°κ³Ό = μ°Έ
    assertThat(result.size()).isEqualTo(3);
    //μ€νκ²°κ³Ό = κ±°μ§(μλ¨)
    }
```

* β λ¬Έμ  λ°μ β  
![image](https://user-images.githubusercontent.com/77817094/174252231-d9336664-e87a-4d02-9caa-b6b1439282bd.png)  

    > μ μ²΄ νμ€νΈλ₯Ό μ€ννκΈ° μν΄μ classλ¨μλ‘ runμ νκ²λλ©΄ νμ€νΈλ€μ μλ κ°μ²΄κ° μ΄λ¦μ΄ κ°μΌλ©΄ (λ€λ₯Έμ  κΈ°μ€ λ¨Όμ  μ μλ μ κ° μμΌλ©΄) μ€νμ€λ₯κ° λ¬λ€. λ°λΌμ testκ° νλ λλ λλ§λ€ λ©λͺ¨λ¦¬λ₯Ό λ¦¬μν΄μ€μΌνλ€. = λ¦¬ν¬μ§ν λ¦¬λ₯Ό μ§μμ£Όλ μ½λ λ£κΈ°.  

* κΈ°λ₯ μμΉ  
![image](https://user-images.githubusercontent.com/77817094/174253843-7288a662-f0a7-4d82-9355-39e87a823dbd.png)  

```java  
@Override
public List<Member> findAll() {
    return new ArrayList<>(store.values());
    //μ€ν μ΄μ μλ λ©€λ²λ€μ λ°νν¨.
}

// μ¬κΈ°μ μΆκ°ν΄μ£ΌκΈ°
public void clearStore() {
    store.clear();
}
```
* μ€ν μμΉ  
![image](https://user-images.githubusercontent.com/77817094/174254443-2c08f426-8c1a-4a1b-89ee-f5fa6847bb79.png)  

```java
@AfterEach //λ©μλκ° μ€νλλ λλ§λ€ λμνλ μ½λ°±λ©μλ
public void afterEach() {
    repository.clearStore();
}

@Test //μ¬κΈ° μμ―€μ μμ± (λ©μλ)
public void save(){
    //λΈλΌλΈλΌ
}
```  

> νμ€νΈ μ½λ μμ΄ κ°λ°νλ κ±΄ κ±°μ λΆκ°λ₯νλ€. νμ€νΈ μ½λλ κ°λ° μ μ λ§λ€μ΄λ λκ³ (TDD) μ΄νμ λ§λ€μ΄λ λλ€. λ§λλ‘~

### π νμ μλΉμ€ κ°λ°π  

νμ μλΉμ€ κ°λ°  
![image](https://user-images.githubusercontent.com/77817094/174262623-73217372-35a6-4732-9741-229dd09d3953.png)  

π¦νμκ°μνλ κΈ°λ₯π¦

```java
package hello.hellospring.service;

import hello.hellospring.domain.Member;
import hello.hellospring.repository.MemberRepository;
import hello.hellospring.repository.MemoryMemberRepository;

import java.util.Optional;

public class MemberService {

    private final MemberRepository memberRepository = new MemoryMemberRepository();

    //νμκ°μ
    public Long join(Member member){
        //κ°μ μ΄λ¦μ΄ μλ μ€λ³΅ νμμ μλ¨.
        //λ°©λ² 1
        Optional<Member> result = memberRepository.findById(member.getId());
        //= μμ μμ°κ³  λ§¨λ€μμ alt+enter+v λλ₯΄λ©΄ μ΅μλ λ­μκΈ° μ κ±° μκΉ.
        result.ifPresent(m -> {
            throw new IllegalStateException("μ΄λ―Έ μ‘΄μ¬νλ νμμλλ€.");
        });
        //result κ°μ΄ μμΌλ©΄ m λ©μΈμ§ μΆλ ₯

        //λ°©λ² 2
        memberRepository.findById(member.getId()).ifPresent(m -> {
            throw new IllegalStateException("μ΄λ―Έ μ‘΄μ¬νλ νμμλλ€.");
        });
        //μ λ¦¬ν΄μ result μλ΅ν΄μ£Όκ³  κ°κ²°νκ² μ§λκ² λ μ’μ λ°©μ!

        memberRepository.save(member);
        return member.getId();
    }

}
```  
 * μ¬κΈ°μ λ³΄λ©΄  
    ```java
    memberRepository.findById(member.getId()).ifPresent(m -> {
            throw new IllegalStateException("μ΄λ―Έ μ‘΄μ¬νλ νμμλλ€.");
        });
    ```
    μ΄λ°μμΌλ‘ λ‘μ§μ΄ μλ μ λ λ©μλλ‘ λ½λκ² μ’μ!

βmethod λ½κΈ°β  
> λ¨μΆν€: λλκ·Ένκ³  alt + enter  
> μλλ©΄ μμ μ κ΅¬ λλ₯΄κΈ°!    

![image](https://user-images.githubusercontent.com/77817094/174264593-ed6602c6-a81f-4b03-a0b0-1c6fb323b5f9.png)

> λ°λ‘ μμ±νκ³  μΆμΌλ©΄ ctrl + alt + m  

![image](https://user-images.githubusercontent.com/77817094/174265386-41b1bba4-acc9-4f0d-927c-9cf2844df7bd.png)  

μ΄μ  μ΄λ¦ λ°κΏμ£Όλ©΄ μ΄μκ² μμ±.
![image](https://user-images.githubusercontent.com/77817094/174265850-558dfb1a-ed5f-435c-b17f-303bf1803b0c.png)


π¦μ μ²΄ νμ μ‘°ννλ κΈ°λ₯π¦

* μκΉ μ κΈ°μ μ΄μ΄μ μΆκ° ν΄μ£ΌκΈ°.
```java
//μ μ²΄ νμ μ‘°ν
public List<Member> findMembers() {
    return memberRepository.findAll();
}

public Optional<Member> findOne(Long memberId) {
    return memberRepository.findById(memberId);
}
```

β¨μμλκΈ°β¨
> λ¦¬ν¬μ§ν λ¦¬λ κ·Έλ₯ λ¨μν μ μ₯μμ λ£μλ€ λΊλ€νλ λλμ΄λκΉ κ·Έλ₯ κΈ°κ³μ μΌλ‘ κ°λ°μ€λ¬μ΄ λλμ μ΄λ¦μ μ§μ΄μ£Όκ³ , μλΉμ€ ν΄λμ€λ λΉμ§λμ€μ μμ‘΄νλ μ λκΉ λΉμ§λμ€μ κ°κΉκ² μ΄λ¦μ μ§μ΄μ€μΌ ν¨.

### π νμ μλΉμ€ νμ€νΈπ
