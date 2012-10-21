{
    "title": "welcome to hero :-)",
    "author": "Rhio Kim",
    "date": "2012-10-20T05:09:58.909Z",
    "categories": [
        "diary"
    ],
    "tags": [],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-10-20T05:09:58.909Z",
    "status": "draft",
    "important": false,
    "advanced": {
        "codeStyle" : "tomorrow-night-bright"
    }
}

## haroopress

![cover](./@img/logo.jpg)

## 주된 기능

* 경량의 문서 작성 포맷인 마크다운을 적용
* 웹 서버와 데이터베이스 시스템이 필요 없음
* 웹 프리젠테이션 기능을 제공
* 클라우드 블로깅으로 언제 어디서든지 블로깅이 가능
* 멀티 마크다운 일부 지원
* 펜스 코드 블럭, 확장 마크다운 문법 제공

## 하루프레스의 작지만 중요한 목표

> 하루프레스의 가장 중요한 목표는 블로그가 필요한 사람들보다 글을 쓰는데 불필요한 서버 구성, 데이터 베이스 설치 등을 잊고 글 쓰는 곳에만 몰입할 수 있도록 하는데 있다.

## Node.js

* 순도 99.9% 하루프레스는 자바스크립트로 작성 (HTML, CSS 제외)
* 백엔드, 프론트 엔드 모두 한 가지 언어
* 약 20개의 노드 모듈로 이루어져 있고, 코어는 약 900 라인

## 5분설치

* 간단한 명령어로 5분 설치

> `$ git clone git@github.com:rhiokim/haroopress.git`
> 
> `$ make init`

## No! 서버, No! 데이터베이스

* 기존의 블로그와 달리 서버와 데이터베이스가 필요 없다.
* 정적 페이지 기반의 블로그 엔진

## 멀티 마크다운 지원

* 전형적인 마크다운에 비해 향상된 마크다운을 일부 제공
* [테이블, 트리플 강조(Triple Emphasis), 자동 링크](http://haroopress.com/post/haroopress-v0-dot-9/)

#### 테이블
이름 | 나이 | 발표 내용
----------|-------|--------------
리오 | 33 | 우리가 모르는 노드로 할 수 있는 몇가지
소리 | ?? | 

#### 트리플 강조 구문
> ***info <i class="icon-info-sign icon-white"></i> 참고사항*** 글을 작성하다보면 다양한 형태의 강조 형식을 사용하게 된다. 그런데 대부분 볼드처리를 하거나 밑줄을 긋거나 색상을 바꿔 처리하는 것이 대부분이다. 물론 그런 방법도 있지만 하루프레스에서는 간단한 ***inverse <i class="icon-refresh"></i> 강조 문법***을 제공하여 좀더 독자가 좀더 쉽고 적절하게 인지할 수 있게 한다.
> ***success <i class="icon-ok-sign"></i> 필독사항*** 꼭 읽어야 할 내용에는 ***success 필독*** 마크를 추가하고 싶어지기도 하다.
>
> ***important 중요사항*** 새로 업데이트 된 내용이 있어서 꼭 알리고 싶은 내용이 있을 때는 ***important 중요*** 마크를 추가할 수도 있다.
> 
> ***warning <i class="icon-warning-sign"></i> 경고성 문구에 강조하는 방법은 warning 을 사용한다.*** 
 

## 마크다운 웹 프리젠테이션

* 간단한 마크다운 문서가 멋진 웹 프리젠테이션
* [언제 어디서든지 웹을 통한 멋진 프리젠테이션](http://haroopress.com/slides/hello-world/)
* 현재 이 페이지도 마크다운으로만 작성된 프리젠테이션

![image](./@img/presentation.png)

## 커스텀 마크다운

* 확장된 마크다운 문법으로 **twitter, youtube, jsfiddle** 등의 콘텐츠를 손쉽게 추가할 수 있다.
* `[youtube:ax0Zsk3]`, `[jsfiddle:ccw9dz]`, `[tweet:1209399932479234]`

#### 유튜브
[youtube:9bZkp7q19f0 100% 420px]

#### 트윗
[tweet:257651670421491712 center]

#### 코드 샌드 박스(JSFiddle)
[jsfiddle:ccWP7]

## 펜스 코드 블럭

* [highlight.js](http://softwaremaniacs.org/soft/highlight/en/) 라이브러리를 사용
* 52 가지 언어 구문 강조 지원
* 26 가지 유명한 구문 강조 [스타일(코드 테마)](http://softwaremaniacs.org/media/soft/highlight/test.html)을 제공
* [공식 페이지 기사](http://haroopress.com/post/fenced-code-block/)

```js
 function syntaxHighlighting() {
   var n = 33;
   var s = "hi";
   console.log(s);
 }
```

## 테마 지원

* 훌륭한 개발자스러운 테마들

![cover](./@img/theme1.png)
![cover](./@img/theme2.png)
![cover](./@img/theme3.png)

## Thanks

* Author [@rhiokim](http://twitter.com/@rhiokim)
* Contact [rhio.kim@gmail](mailto:rhio.kim@gmail.com)
