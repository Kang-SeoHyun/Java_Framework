# ✏CH2.프로젝트 환경설정✏

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

### 🌟View 환경설정🌟

* Welcome page 만들기  
  * static/index.html을 올려두면 웰컴페이지 기능을 제공함.  
    > 이런거 검색은 spring.io 사이트에서 상단바에서 
    projects -> spring boot -> learn -> 맨위 버전의 Reference Doc  
    들어가서 찾으면 됨
    

* 컨트롤러 만들기
  * main문 있는 곳에 컨트롤러 만들어주고 컨트롤러가 문자를 반환하면 viewResolver가 화면을 찾아서 처리한다.  
    * > resources / templates / {반환값이름(ViewName)} + .html  
    ex) hello.html ![image](https://user-images.githubusercontent.com/77817094/173014541-34525458-2dc5-49ee-8d7e-f3c2253e4902.png)
  * 동작 환경 그림 ![image](https://user-images.githubusercontent.com/77817094/173014706-8db0adaa-fcbc-4f79-815b-9be4d5d97a2a.png)  


### 🌟build하고 실행하기🌟  
실제 console 창에서 build 하는 법  
1. root file로 찾아간다.  
2. 명령어 : ./gradlew build 입력 (삭제는 clean 입력)  
3. build 파일이 생성되면 cd/build/libs 해서 jar파일 생성되었는지 확인 후  
4. 명령어 : java -jar {파일이름(ex.hello-0.0.1-SNAPSHOT)} .jar 입력  
5. 실행 확인