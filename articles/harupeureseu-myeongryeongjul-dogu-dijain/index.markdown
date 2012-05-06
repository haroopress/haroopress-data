{
    "title": "하루프레스  명령줄 도구 디자인",
    "author": "Rhio Kim",
    "date": "2012-04-28T02:16:21.722Z",
    "categories": [
        "haroopress",
        "diary"
    ],
    "tags": [],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-04-28T02:16:21.722Z",
    "status": "public",
    "important": false,
    "advanced": {}
}

## 하루프레스 명령줄 도구
<img src="./@img/cli.png" class="pull-left thumbnail" />

아무래도 하루프레스에는 명령줄 도구가 필요해. 그것도 잘 디자인된 명령줄이면 더 좋을것 같아.

일단 명령줄 도구(Command Line Tool)란?
> 콘솔 혹은 터미널 상에서 명령어를 입력해서 하루프레스를 사용하는 것이지. 쉽게 말하면 GUI 반대말이라고도 할 수 있지. 마우스 클릭 만으로 사용할 수 있는 그래픽 요소는 전혀 없다는 말.


하루프레스와 같이 해커들을 위한 블로그 엔진 성격과 GUI 는 좀 어울리지 않아.
그래서 NPM 으로 명령줄 도구를 만들기로 했지.

### 명령줄 네이밍 디자인
먼저 하루프레스에서 사용하는 기능들에 대한 정의가 필요해. 이미 `v0.8.2` 를 향해 달려가고 있는 중이라 대부분의 주요 기능들은 구현된 상태라고 할 수 있지. 뿐만 아니라 이미 Make 로 작성된 것들이 있어서 그것을 기반으로 하면 되.

* 초기화
* 글 작성
* 페이지 작성
* 정적페이지 생성
* 미리보기
* 배포

이 정도면 하루프레스를 이용하는 사용자에게 기본적인 도구는 되겠어 좀더 디테일한 기능은 앞에 6가지가 완료되면 더 넣기로 하고 일단 완료.

그럼 위의 기능들이 실제로 하루프레스에서는 어떤 이름을 갖게 되면 좋을까? 하루프레스랑 동떨어지면 안되고 명령줄 도구는 자주 사용하게 될테니 하루프레스를 각인시키기 위해서 **haroopress** 로 해야겠다.

* haroopress init
* haroopress new post
* haroopress new page
* haroopress generate
* haroopress preview
* haroopress deploy

음… 그런데  좀… 길어. 아무리 각인 시킨다지만 너무 긴건 짜증나니까. 풀 네이밍을 저렇게 가져가되 축약 명령도 만들어야 겠어.

* haroo init
* haroo new post
* haroo new page
* haroo gen
* haroo preview
* haroo deploy

의미를 유지하면서 축약한거니 거부감도 없고 하루프레스에 대한 인식도 어느정도 유지될 꺼라고 본다.

### 상세 기능 정의
명령어는 마음에 들게 정해졌지만 구현해야 할 기능들은 굉장히 많네. 그럼 좀더 상세하게 기능을 정리해 봐야겠다.

#### haroo init
> 하루프레스를 정적 페이지를 생성해주고 깃헙 저장소로 배포하는 것등을 자동화 해주기 때문에 깃헙 저장소에서 클론(clone) 한 후에 사용자 컴퓨터 환경에 맞게 동작할 수 있어야 하니까 초기화를 해주어야 겠지.

* GIT 서브 모듈 초기화
* NPM 의존성 모듈 설치
* 블로그 메타 정보
* 하루프레스 환경설정
* 배포 경로 설정

초기화에 생각보다 할 것이 많네. 일단 하나의 타스크별로 모듈을 구현을 하자. 그래야 타스크 조합을 통해 좀더 복잡한 처리에 유연하게 동작할 수 있을 테니. 그리고 재활용도 가능할 꺼고.. 예를 들면 초기화를 진행한 후에 배포 경로만 다른 곳으로 변경한다거나 환경설정을 새롭게 한다거나 할 수 있을테니

#### haroo new post

새로운 글을 작성하려면 하루프레스에 맞춰진 구조화된 위치에 임시 파일을 생성해주어야 해.  `config.js` 환경설정 파일에 정의된 경로를 기준으로 파일을 생성해주면 되겠지.

예를 들면 다음과 같은 스텝으로 진행하면 좋을거 같아.

```
$ haroo new post 
haroo> insert article's title : haroopress install guide
haroo> insert article's category : haroopress, tutorial, guide
haroo> insert article's tag : haroopress

haroo> created to path/to/article/dir/haroopress-install-guide.markdown
```

위의 스텝으로 진행해서 최종적으로 markdown 이 생성되고 해당 markdown 을 편집하면 되겠지.

근데 몇가지 고려해야 할 사항이 있어.

1. 이미지가 포함된 포스팅일 경우를 대비
2. 실행형 자바스크립트가 포함될 경우를 대비
3. 마크다운 파일명 규칙

<img src="./@img/unicode2ascii.png" class="pull-right thumbnail" />

파일명 규칙에는 특히 중요한 이슈가 있는데 파일 제목이 영어라면 띄어쓰기 문자를 '-' 하이픈으로 치환해 버리면 되지만 만약 한글이면 처리할께 많아진다. 

만약 포스팅 제목을 "하루프레스 설치 가이드" 라고 했다고 하면 파일명은 '하루프레스-설치-가이드.markdown' 이 될꺼고 정적페이지로 출력되어 웹 서비스될 때는 브라우저에서 유니코드로 자동 변환 할 텐데… 
그러면 URI 가 깨지니 개선이 필요할 것 같아.

유니코드(Unicode)를 아스키코드(ASCII) 로 변환해주는 작업을 해야겠군

"하루프레스 설치 가이드" 가 'haroopress-seolchi-gaide.markdown' 형태로 되면 한글의 경우 파일명이 어색하기는 하지만 URI 도 좀더 낫다고 본다.


#### haroo new page
페이지 생성은 포스팅과 유사하지만 별도의 레이아웃 구조만 갖도록 처리하자.
작성예정...

#### haroo gen
작성예정...

#### haroo preview
캬캬! 하루프레스 미리보기는 정적 페이지를 생성해서 HTML 파일을 웹 서버를 띄워 그대로 보는 것이기 때문에 구현해야 할 기능은 굉장히 간단하다. 

* 노드 기반의 로컬 웹 서버 구동
* 브라우저를 실행한다.

이것은 이미 만들어 놓은 [locally][1] 를 이용하면 되겠다.
>  [로컬리(locally)][1] 는 haroopress 와 같이 명령줄 도구로 `locally` 명령을 통해 현재 위치한(pwd) 경로를 웹 루트로 하여 웹 서버를 구동시켜주는 노드 기반의 모듈이다. 자세한 사용법과 옵션은 깃헙 저장소에서 확인하세요.


#### haroo deploy 
작성예정...

[1]: http://github.com/rhiokim/locally