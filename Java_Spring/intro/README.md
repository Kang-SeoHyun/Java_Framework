# 💡기억하기💡

## 🧸gradle 실행 방법🧸
  1. java코드에서 main문을 실행  
     > file -> project structure에서 언어 build.gradle이랑 맞춰서 잘 설정 되어있는지 확인하기.
  2. 실행되면 웹 브라우저 실행해서 localhost:8080 실행하기.   


## 🧸intellij git 연결🧸
  1. 터미널창에서 깃 레포지토리 clone
  2. open project할때는 전체말고 젤 상위 폴더만  
  3. 작업 끝나면 터미널창에서 git push  

## 🧸실제 console 창에서 build 하는 법🧸  
  1. root file로 찾아간다.  
  2. 명령어 : ./gradlew build 입력 (삭제는 clean 입력)  
  3. build 파일이 생성되면 cd/build/libs 해서 jar파일 생성되었는지 확인 후  
  4. 명령어 : java -jar {파일이름(ex.hello-0.0.1-SNAPSHOT)} .jar 입력  
  5. 실행 확인