{
    "title": "gravatar image",
    "author": "Rhio Kim",
    "date": "2013-02-16T04:14:51.875Z",
    "categories": [
        "tutorial"
    ],
    "tags": [
        "haroopress",
        "gravatar"
    ],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2013-02-16T04:14:51.875Z",
    "status": "publish",
    "important": false,
    "advanced": {
        "codeStyle": "solarized_light"
    }
}

Gravatar(이하 그라바타) 서비스를 모르는 분들이라면 하루프레스를 처음 설치하고 뜨는 아래의 이미지를 보고 '바꿀 수 없을까?' 라는 의문을 품을 것이다.

![Gravatar 기본 이미지](http://www.gravatar.com/avatar/a8618a255192bd842fdd62d099776735?r=pg&s=175.jpg&d=identicon) 

물론 [그라바타](http://ko.gravatar.com/) 서비스를 이용해 이미지만 변경하여 나만의 이미지로 변경할 수 있다.

### Gravatar?

> Gravatar는 블로그에 글을 쓰거나 댓글을 쓰는 것 같은 일을 할 때 이름 옆에 나타나서 사이트마다 당신을 따라다니는 그림이에요. 아바타는 블로그나 웹 포럼에 올라온 당신의 글들을 확인하는 것을 도와줘요. 모든 사이트에서 안 될 이유가 있나요? <small>http://ko.gravatar.com/</small>

우리는 많은 서비스들에서 자신의 아이덴티티를 표현하는 아이디와 이미지(아바타)를 대부분 갖고 있다. 이점에 타겟팅을 한 서비스이다.

WordPress, Github, Disqus, Stackoverflow 등 다양한 곳에서 그라바타 서비스를 이용중에 있다.

### 그라바타를 등록

이미 커뮤니티를 통해 작성된 좋은 메뉴얼들을 참고하면 되어 여기에서 별도의 설명은 없다. 
사실 방법이 그리 복잡하지도 않다. 

* [GRAVATAR 그라바타](http://ilmol.com/web101/gravatar) <cite> via http://ilmol.com/web101/gravatar</cite>

### 하루프레스에서는 어떻게?

하루프레스의 특징은 모든 데이터가 `JSON` 혹은 `Markdown` 이다. 이점은 꼭 기억해두는 것도 좋다.

파일 탐색기를 열고 하루프레스 설치 디렉토리로 가보자.

#### 구조의 이해

`source/data` 디렉토리를 살펴보면 다음 구조로 되어있다.

```
 + articles
 + authors
 - favorites.markdown
 + pages
 + slides
```

디렉토리에 대한 부연 설명을 간단히 하자면 다음과 같다.

* articles : 포스팅 Raw 데이터 디렉토리
* authors : 저작자 정보 디렉토리
* favorites.markdown : 즐겨찾기 파일
* pages : 페이지 형태의 포스팅 디렉토리
* slides : 슬라이드 형태의 포스팅 디렉토리

이제 그라바타를 적용을 해보자.

#### 적용방법

`authors` 로 들어가면 `haroopress.markdown` 파일과 처음 설치 과정중에 입력한 본인의 영문 이름으로 된 markdown 파일이 2개 존재할 것이다.

여기서 본인의 영문 이름으로 된 markdown 파일을 열어보자.

**{자신의 영문이름}.markdown**

```js
{
    "name": "화면상에 표시될 이름",
    "company": "회사 이름",
    "blog": "블로그 주소",
    "twitter": "haroopress",
    "github": "haroopress",
    "vimeo": "",
    "youtube": "",
    "facebook": "",
    "linkedin": "",
    "email": "그라바타 등록에 사용한 이메일 주소"
}

자기소개를 자유롭게 작성해주세요.
```

그라바타를 반영하기 위해 `email` 부분에 등록 시 사용한 이메일을 기재해 주면 된다. 기타 필요한 정보를 입력해두면 좋다.

저장이 완료되었다면 `make preview` 를 통해 반영되었는지 확인해보자.