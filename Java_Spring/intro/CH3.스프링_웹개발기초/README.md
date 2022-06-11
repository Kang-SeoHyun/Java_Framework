# 🎀CH3.스프링 웹 개발 기초🎀

### 🌟정적 컨텐츠🌟  
> 고객에게 파일을 그냥 그대로 전달      

* 만드는 방법  
    ![image](https://user-images.githubusercontent.com/77817094/173174974-c3ab253b-fcc4-46c8-a4ad-67d989c2e9df.png)  
이런식으로 html 파일 작성하면 저 파일이 그대로 홈페이지에 나오는데 이런걸 정적 컨텐츠라고 한다.  
![image](https://user-images.githubusercontent.com/77817094/173175053-074240c8-fef5-4507-9760-4c16ad493c9f.png)

### 🌟MVC와 템플릿 엔진🌟  
> Model, View, Controller  
> 서버에서 조금 변환해서 고객에게 전달 - 요새 많이 사용  
> > ex) 템플릿 엔진: jsp, php같은거
  
예전엔 뷰랑 컨트롤러만 있었음.  
뷰는 화면을 그리는데 모든 역량 집중해야함.  
따라서 모델 뷰 컨트롤러로 쪼갬.  

* 만드는 방법  
![image](https://user-images.githubusercontent.com/77817094/173175587-f6221439-b660-444d-b155-28b3168b79d1.png)  
이런식으로 컨트롤러에 하나 추가해주고 리턴값.html 파일을 템플릿에 만들어준다.  
     > ![image](https://user-images.githubusercontent.com/77817094/173175645-5e18070e-1c44-44a7-8408-a1aa1319dfef.png)  
     타임리프 템플릿의 장점은 서버를 돌리지않고도 껍데기를 확인할 수 있는 것이다. 그때는 마크업을(여기서는 hello! empty 이부분) 해두어서 결과를 예측 할 수 있다.

    그러면 name에 값이 존재할때 작동하는 것을 볼 수 있다.  
    > name에 값 없을 때  
    ![image](https://user-images.githubusercontent.com/77817094/173175919-524e242c-012d-48b8-9b30-f8c1b3c53e49.png)  
    > name에 값 있을 때  
    ![image](https://user-images.githubusercontent.com/77817094/173175907-dbe7a21b-d021-4d2c-a6e7-4bd78726e506.png)  
    --- '?name=seohyun'으로 넣어줌  

* 동작 이미지  
![image](https://user-images.githubusercontent.com/77817094/173175999-8381ce68-ed9c-4565-8bef-d2bf9ee923e0.png)  
<pre>
뷰리졸버(뷰를 찾아주고 템플릿엔진 연결하는 놈)가 리턴값.html을 찾아서 템플릿엔진(여기선 타임리프엔진)한테 처리해달라고 넘김. 그럼 템플릿엔진이 렌더링을 해서 변환을 한(정적컨텐츠와의 차이) html을 웹 브라우저에 넘김!
</pre>

### 🌟API🌟  
> json이라는 데이터 구조 포맷으로 고객에게 전달  
> > ex) 데이터가 흐를때 많이 사용함  

* 만드는 법 (맛보기)  
    * 컨트롤러에 아래 코드 추가
    ```java
    @GetMapping("hello-string")
    @ResponseBody //http에서 바디부에 이 데이터(리턴값)를 직접 넣겠다 의미
    //밑에 동작이미지에서 설명
        public String helloString(@RequestParam("name") String name) {
        return "hello " + name;
    }
    ```

    얘는 그대로 html태그고 뭐고 그냥 그대로 출력함.  
    * mvc로 만든 화면 소스코드
    ![image](https://user-images.githubusercontent.com/77817094/173177844-40908c32-7232-426e-bb94-0278e806632e.png)  
    * api로 만든 화면 소스코드
    ![image](https://user-images.githubusercontent.com/77817094/173177830-f4a1e3f3-a853-414a-8909-3debc293318a.png)  

* 만드는 법 (진짜)  
    * 컨트롤러에 아래 코드 추가
    ```java
    // 문자말고 데이터 내놓으라 할때를 위해 api씀
    @GetMapping("hello-api")
    @ResponseBody
    public Hello helloApi(@RequestParam("name")String name){
        Hello hello = new Hello();
        hello.setName(name);
        return hello;
    }

    static class Hello {
        private String name;

        //단축키: Ctrl + n
        //Getter Setter 찾아서 ok 누르면 자동 입력됨. 
        public String getName() {
            return name;
        }

        public void setName(String name) {
            this.name = name;
        }
    }
    ```  
    
    * 출력화면  
    ![image](https://user-images.githubusercontent.com/77817094/173178516-b0900650-9276-42a9-aa4f-6c9bd1bda8cc.png)  
    이건 json이라는 방식임. (key, value로 이뤄짐)  
    최근에 많이 사용. (이전엔 xml사용 - 그 태그 쓰는거)  

* 동작 이미지  
![image](https://user-images.githubusercontent.com/77817094/173178856-1fd10288-6535-4d32-ab00-0fb66c171e54.png)  
-> @ResponseBody 사용 원리  
    <pre>
    @ResponseBody가 오면 http응답에 그냥 return데이터를 넘겨야겠다고 반응함. 근데 그 return값으로 객체가 오면 기본 디폴트값이 json형식으로 데이터를 만들어서 http응답에 반응함.  
    (기존에 뷰리졸버가 반응했다면 지금은 HttpMessageConverter가 반응함.-객체면 JsonConverter가 반응함) 
    </pre>  
    참고하기.
    > ![image](https://user-images.githubusercontent.com/77817094/173183957-bdc17295-8a1d-475e-9cf1-25b77fdcbaa0.png)  
    객체를 Json으로 바꿔주는 유명한 라이브러리가 2개있음. (하나가 jackson 나머지가 구글에서 많이 쓰는 쥐쓴)  
    스프링은 jackson이라는 라이브러리 넣어둠!