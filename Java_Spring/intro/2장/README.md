## [프로젝트 생성](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-%EC%9E%85%EB%AC%B8-%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8/lecture/48553?volume=1.00)

* 스프링 기반 프로젝트 만들어주는 [사이트](https://start.spring.io/)  
    1. 요즘 Gradle project 많이사용  
    2. spring boot는 젤 최근꺼 사용  
    3. metadata에서 artifact는 플젝이름 같은거 쓰면 됨  
    4. dependencies에서 spring web 이랑 thymeleaf(html 템플릿) add하기  

![image](https://user-images.githubusercontent.com/77817094/172542397-388cea84-6d91-450e-9e9c-9e0e56d194c5.png)  
* gradle - gradle 관련 폴더  
* src - main이랑 test폴더 나뉘어 있음  
    * main아래 java 
    > 실제 패키지, 소스파일  
    * main아래 resorces 
    > 자바이외코드들어감 - 설정코드 or html코드같은
    * test아래 
    > 테스트코드와 관련된 소스들이 들어감  
    > 테스트코드 중요성 알 수 있음
* build.gradle  
    * gradle 설정파일 
    > io사이트에서 자동으로 만들어줌  
    > '버전설정하고 라이브러리 땡겨오는구나' 정도 알면 됨
