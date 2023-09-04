# Repository : crawler
## 목적 : 간단히 사용할 수 있는 크롤러를 만들어본다.
## 환경 : MacOS M1
### 1️⃣ Jsoup을 이용한 크롤링 (정적 html 크롤링)
#### 활용한 라이브러리
```groovy
    implementation group: 'org.jsoup', name: 'jsoup', version: '1.16.1'
```
#### 예시 코드 (자세한 코드는 내용 확인하기!) - 준비중 (조금만 나중에 올릴게요 ㅎㅁㅎ;;)

### 2️⃣ Selenium을 이용한 크롤링 (동적 html 크롤링)

#### 준비사항 : selenium-server-{버전}.jar파일, chromedriver
#### 순서
 1. selenium server(Grid) 다운로드 > https://www.selenium.dev/downloads/
 2. chrome 자동 업데이트 끄기(터미널에 입력) 입력 후, 터미널 재실행 또는 변경된 내용 적용하기 > defaults write com.google.Keystone.Agent checkInterval 0
 3. (참고) chrome 자동 업데이트 켜기(터미널에 입력), 터미널 재실행 또는 변경된 내용 적용하기> defaults write com.google.Keystone.Agent checkInterval 18000
 4. chromedriver 다운로드 > https://chromedriver.chromium.org/downloads

#### 주의사항1. selenium-server jar 파일과 chromedriver 버전이 맞아야 한다.
- chromedrvier 113과, selenium-server-4.12.0.jar 연결 가능
  <br>
#### 주의사항2. chromedriver 버전과 chrome버전이 맞아야 한다.
- chrmomedriver는 대체로 최신 chrmoe 버전보다 버전이 낮은 경우가 있는 것 같다. 따라서 다운 그레이드가 필요할 수 있다.
  다운그레이드는 OS에 맞게 다음의 사이트에서 다운로드 후 설치하면 된다. > https://google-chrome.en.uptodown.com/windows/versions
  cf. 다시 자동업데이트를 설정하려면 
- 크롬 자동업데이트가 되는 것을 막아놓아야 하는데 (안그러면 계속 다시 깔아야 한다.) 
- chrmoedriver 113을 이용한다면 chrome 버전도 113이어야 한다.
- 크롬 버전 정보 확인 > chrome://settings/help


#### 예시 코드 (자세한 코드는 내용 확인하기!) - 준비중 (조금만 나중에 올릴게요 ㅎㅁㅎ;;)





#### 활용한 라이브러리
#### 2️⃣ Selenium jar 파일 임포트
```groovy
implementation files('{jar 파일 경로}/selenium-server-4.12.0.jar')
 ```

--- 
### 아래 부분은 수정 예정
### 활용한 API
정보 도서나루 공개 API의 **정보공개 도서관API**<br>  
> 활용 API 예시 : http://data4library.kr/api/libSrch?authKey=[발급받은키]&pageNo=1&pageSize=10<br>  

<h3>클래스 구성</h3>
(class) AppConfig : CSVMaker, BookDataCralwer를 빈 등록, Value값을 불러옴  <br>
(interface) DataCrawler : getCrawledData,() extractData(). <br>  
(class) BookDataCrawler : DataCrawler를 구현한 클래스. <br>  
(class) SSLUtil : 공개 도서나루 Api에 요청을 보낼 때, 인증서 신뢰를 시키게 하기 위한 클래스 (보완 필요)  <br>  
(class) CSVMaker : BookDataCrawler의 extractData를 활용하여 크롤링 한 이후, CSV 파일 생성  <br>  
(class) CSVMaker2 : BookDataCrawler의 extractData를 활용하여 전체 데이터에 대해 크롤링 이후, CSV 파일 생성  <br>  
(class) StartCrawling : 크롤링 실행 <br>
