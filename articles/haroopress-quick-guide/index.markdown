{
    "title": "하루프레스 퀵 가이드",
    "author": "Rhio Kim",
    "date": "2012-05-21T05:36:02.635Z",
    "categories": [
        "tutorial"
    ],
    "tags": [],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-05-21T05:36:02.635Z",
    "status": "public",
    "important": true,
    "advanced": {}
}

이 문서는 [하루프레스][haroopress] 설치를 위한 퀵 가이드로 Step-by-Step 으로 진행됩니다.
기타 문의 사항은 [rhio.kim+haroopress@gmail.com](mailto:rhio.kim+haroopress@gmail.com) 으로 메일 주세요.

## 기본 요구사항

### Node.js
노드는 0.6.x 이상의 최신 버젼을 유지하길 권장드립니다. 

* [http://nodejs.org](http://nodejs.org)

노드는 현재 빠르게 개발이 진행중인 오픈소스 프로젝트로 버젼 업데이트가 자주 발생하기 때문에 소스를 바로 빌드하는 것보다 루비의 `rvm` 과 같은 노드의 `nvm` 을 이용하는 것이 좋습니다. 아래를 참고해주세요.


#### 노드 버젼 메니저
노드 버전 메니저인 `nvm` 을 이용하면 좀 더 쉽게 노드를 설치 및 관리할 수 있습니다. 자세한 설치와 사용 방법은 아래의 링크에서 확인하세요.

* [https://github.com/creationix/nvm](https://github.com/creationix/nvm)

### Git
[하루프레스](haroopress) 엔진은 노드와 6가지의 오픈소스의 조합으로 만들어졌습니다. 그렇다 보니 코어 엔진을 제외한 대부분의 모듈들이 Git 서브 모듈로 관리되고 있습니다.  

물론 [하루프레스](haroopress)도 Git 을 통해 관리되고 있습니다.  아래 공식 사이트에서 각 운영체제에 맞는 버젼을 설치하세요.

* [http://git-scm.com/](http://git-scm.com/)

### 지원 운영체제
현재 [하루프레스](haroopress)는 맥 운영체제에서만 테스트가 되어지고 있고 윈도우와 리눅스 지원 여부는 향후 추가할 예정입니다.  오픈 소스이니만큼 유저들의 경험이 피드백이 된다면 좀더 빠르게 발전할 수 있습니다.

* Mac OS X
* <del>Linux</del>
* <del>Window</del>

위의 기본 요구사항이 충족되었다면 이제 직접 설치를 해봅니다.

## 하루프레스 설치하기
Git 이 설치되었다면 설치는 사실 굉장히 단순합니다. Github 의 소스를 클론(clone)만 하면 되기 때문입니다.

### 소스 복제
소스 복제할 때에는 아래와 같이 복제할 위치를 사이트명으로 해주는 것도 좋습니다.

```
// Github.com 의 소스를 내 PC 로 복제합니다.
$ git clone git@github.com:rhiokim/haroopress.git /path/to/[domain]
$ git clone git@github.com:rhiokim/haroopress.git /path/to/aaa.mysite.com
```

### 초기화 및 하루프레스 환경설정
설치 역시 너무 단순합니다. 

```
// aaa.mysite.com 엔진 초기화 및 환경설정
$ cd /path/to/aaa.mysite.com
$ make init
. . .
설치과정
. . .
haroo> Please! insert your blog title 
haroo> Please! insert your blog description
haroo> Please! insert site url (e.g. http://site.com)
haroo> Author Name? `Rhio Kim`
/path/to/source/data/authors/`Rhio Kim`.markdown
haroo> Meta Keyword?
```
설치는 `make init` 명령 하나면 모든 것이 끝이지만 설치 과정에 어떤 일들이 일어나는지 알아두는 것도 하루프레스 해커가 되려면 꼭 필요합니다. 

다음과 같은 과정이 진행됩니다.

1. npm 서브모듈 설치
2. git 서브모듈 업데이트와 초기화
3. git 서브모듈 빌드
4. 하루프레스 환경설정
5. 배포용 Github 저장소 - 실제로 웹 페이지가 동작할 저장소
6. 하루프레스 폴더 및 데이터 스켈레톤 생성

환경설정 및 초기화가 완료되었다면 바로 정적 페이지를 생성해보자.

## 정적 페이지 생성
```
$ cd /path/to/aaa.mysite.com
$ make gen

========================================
= generate to static page
========================================
haroo> cp -R /path/to/aaa.mysite.com/source/themes/wood-dark/public/* /path/to/aaa.mysite.com/_public
haroo> export rss.xml ¶
haroo> /path/to/aaa.mysite.com/_public/rss.xml
haroo> export 404.html ¶
haroo> /path/to/aaa.mysitecom/_public/404.html
haroo> export index.html ¶
haroo> /path/to/aaa.mysite.com/_public/index.html
haroo> export archives.html ¶
haroo> /path/to/aaa.mysite.com/_public/archives/index.html
haroo> export article.html ¶
haroo> /path/to/aaa.mysite.com/_public/post/welcome-to-haroopress/index.html
haroo> export categories.html ¶
haroo> /path/to/aaa.mysitecom/_public/category/index.html
haroo> export category.html ¶
haroo> /path/to/aaa.mysite.com/_public/category/haroopress/index.html
haroo> export authors.html ¶
haroo> /path/to/aaa.mysite.com/_public/authors/index.html
haroo> export author.html ¶
haroo> /path/to/aaa.mysite.com/_public/authors/haroopress/index.html
haroo> export pages.html ¶

// 위와 같이 정적 페이지들이 생성되는 것을 확인할 수 있습니다.
```

## 포스팅하기
```
$ cd /path/to/aaa.mysite.com
$ make new-post
haroo> Enter article title : `포스팅 제목`
haroo> Enter article category (e.g cate1, cate2, cate3 ) : `카테고리를 입력해주세요.`
haroo> Enter article tag (e.g tag1, tag2, tag3) : `테그를 입력해주세요.`

// markdown 파일과 리소스 저장 경로가 생성됩니다.
haroo> write post -> /path/to/aaa.mysite.com/source/data/articles/`포스팅 제목`/index.markdown
haroo> article's image path /path/to/aaa.mysite.com/source/data/articles/`포스팅 제목`/@img
```
위의 로그 중 마지막 두줄을 살펴보면 `index.markdown` 파일과 `@img` 폴더가 생성된 것을 알 수 있습니다. `index.markdown` 은 실제로 포스팅 할 내용을 작성하시면 되고 `@img` 의 경우에는 해당 포스팅 내에 포함될 이미지 경로입니다.

`index.markdown` 파일을 열어보면 기본 데이터 포맷이 이미 정의되어 있습니다.  데이터 포맷에 대한 자세한 사항은 다음 링크를 확인해주세요.

* [하루프레스 데이터 포맷](/post/haroopress-default-data-format)

## 정적 페이지 미리보기
```
========================================
= preview static page
========================================

//로컬 서버가 구동되고 생성된 정적 페이지들을 브라우저에서 확인할 수 있게 됩니다.
haroo> execuate local static webserver¶
haroo> open http://localhost:8081 ¶

Show me on the browser? [y/n] : 
//자동으로 브라우저를 실행시키고 싶다면 y 아니라면 n 을 입력하고 엔터치면 됩니다.
```