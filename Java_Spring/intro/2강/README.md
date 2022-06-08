# ✏2강 - 프로젝트 환경설정✏

### 🌟프로젝트 생성🌟

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

### 🌟라이브러리 살펴보기🌟

* gradle  
    * 의존관계가 있는 라이브러리를 함께 다운로드 한다. 
    <pre>
    프로젝트 만들때 dependencies에서 spring web 이랑 thymeleaf 두개 써서 build.gradle 에는  
    라이브러리 2개만 추가됐지만, 걔네도 사실 필요한 라이브러리가 있고,  
    걔네도 또 있고,,, 그런 엄청 많은 것들을 자동으로 끌어와줌.  
    (intellij에서 오른쪽 끝라인 잘보면 작게 gradle 써있는거 눌러보면 의존성 확인가능!)  
    </pre>
* 스프링 부트 라이브러리  
     ![image](https://user-images.githubusercontent.com/77817094/172610033-ae6ad593-1590-4531-b577-cb0685bc3238.png)

    * spring-boot-starter-tomcat
    <pre>
    요즘은 웹서버 띄우기위해 tomcat서버같은거 다운받고 하는 짓 안함.  
    라이브러리 빌드해서 웹서버올리면 끝남.
    </pre>  
    * spring-boot-starter-thymeleaf : 타임리프 템플릿 엔진(view)  
    * spring-boot-starter  
    <pre>
    실제 현장에선 system.out.print 잘 안쓰고 로그사용함.  
    라이브러리에 포함되어있음(logback 많이사용)
    </pre>  
    
* 테스트 라이브러리  
    ![image](https://user-images.githubusercontent.com/77817094/172611065-6f079b63-3c44-4399-9454-b401955133fb.png)
