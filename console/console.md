- # 효과적인 로그 처리하는 방법

  ## 목차

  ### 1\. 로그 레벨

  ### 2\. 로그 처리하는 방법

  ### 3\. 출처

  ## 1\. 로그 레벨

  로그가 발생한 심각성에 따라서 나눠 놓은 키워드를 로그 레벨이라고 합니다.

  자바스크립트에서는 log, info, warn, error 4가지 정도로 나눌 수 있다.

  #### 1\. console.log\(\)

  * 개발 단계에서 부수적인 데이터를 출력하고자 할 때 사용
  * 대부분 사용
  * 제품을 배포할 때는 보통 지우고 배포

  <img src="https://user-images.githubusercontent.com/66556683/139779728-92fd42f1-ae85-483f-93f1-2402fb862262.png" alt="log" style="margin: 0; zoom:150%;">

  #### 2\. console.info\(\)

  * 특정한 정보를 출력시에 사용
  * 제품을 배포할 때는 보통 지우고 배포

  <img src="https://user-images.githubusercontent.com/66556683/139779835-0c29be99-402f-46b6-9c54-688c6db62fc6.png" alt="info" style="margin: 0; zoom:150%;">

  #### 3\. console.warn\(\)

  * 심각하진 않지만 경보 단계에서 사용

  <img src="https://user-images.githubusercontent.com/66556683/139779954-8d80a2e1-5cfa-4083-a4dc-9587831e0e68.png" alt="warn" style="margin: 0; zoom:150%;">

  #### 4\. console.error\(\)

  * 심각한 에러일 때 사용
  * 오류 메시지를 출력합니다.

  <img src="https://user-images.githubusercontent.com/66556683/139779900-9e88202a-547e-4561-8d28-88255c5c6c2a.png" alt="error" style="margin: 0; zoom:150%;">

  ## 2\. 로그 처리하는 방법

  console.log 는 가장 간편한 디버깅 도구이긴 하지만 운영에 배포되는 어플리케이션에는 포함되지 않는 것이 좋습니다.
  불필요한 코드 이기도 하고 보안 이슈가 발생할 가능성도 있습니다.
  무엇보다 개발자가 신경을 안 썼다는 **티**가 나서 좋지 않습니다.

  #### 1\. 내부객체인 console에 \{\}로 덮는 방법

  ``` javascript
  console.log('초기화 전');
  console.log('log');
  console.warn('warn');
  console.error('error');
  
  console.log('초기화 후');
  console = {};
  console.log = function(){};
  console.warn = function(){};
  console.error = function(){};
  
  console.log('log');
  console.warn('warn');
  console.error('error');
  ```

  <img src="https://user-images.githubusercontent.com/66556683/139780031-7ca9be11-3237-4cf1-8410-efe9ca63d63b.png" alt="log2" style= "margin: 0;"> 

  이 방법을 사용하면 유저가 console을 이용하지 못하게 막을 수도 있다.

  #### 2\. 하나하나 지우기 혹은 주석 처리하는 방법

  ``` javascript
  // console.log('log');
  ```

  자주 사용되지만 많은 console.log가 있을 시에 매우 번거롭다.

  #### 3\. 번들러 Webpack에 있는 모듈babel의 플러그인 babel\-plugin\-transform\-remove\-console 사용하는 방법 (추천)

  * 모드 설정을 통하여 개발할 때에는 console을 출력 되게 하고 배포할 때에는 console의 출력을 지운다.
  * 모드만 바꾸면 되기 때문에 간편하다.

  ## 3\. 출처

  * [https://soheemon.tistory.com/entry/JavaScript-%EB%B3%B4%EC%95%88%EC%9D%84-%EC%9C%84%ED%95%B4-console-%EB%A1%9C%EA%B7%B8-%EB%A7%89%EA%B8%B0](https://soheemon.tistory.com/entry/JavaScript-%EB%B3%B4%EC%95%88%EC%9D%84-%EC%9C%84%ED%95%B4-console-%EB%A1%9C%EA%B7%B8-%EB%A7%89%EA%B8%B0)
  * [https://gitabout.com/3](https://gitabout.com/3)