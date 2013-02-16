{
    "title": "하루프레스의 기본 데이터 규약",
    "author": "Rhio Kim",
    "date": "2012-05-21T09:06:14.490Z",
    "categories": [
        "haroopress"
    ],
    "tags": [],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-05-21T09:06:14.490Z",
    "status": "publish",
    "important": false,
    "advanced": {}
}

이 문서는 하루프레스를 이용하기 위한 블로그 글, 페이지, 작성자 정보등을 다루기 위한 데이터 포맷에 대해 정의합니다.
cli 명령을 제공하기 때문에 헤더 정보를 직접 생성하는 경우는 거의 없으나 상황에 따라 수정 편집해야 하는 경우가 발생하기 때문에
기본 포맷의 구조에 대해서 **꼭** 알아두는게 좋습니다.

### 데이터 포맷 소개
하루프레스의 사용자 생성 데이터는 모두 **JSON** 과 **Markdown** 으로만 이루어집니다.


#### 포스팅
블로그 포스팅 데이터는 두 가지로 분리됩니다.

```
{
  헤더
}

내용
```

##### 포스팅 기본 포맷
```js
{
    "title": "하루프레스 데이터 포맷 소개",    //블로그 제목
    "author": "Rhio kim",                  //작성자
    "date": "2012-05-14T04:33:48.267Z",    //작성 시간
    "categories": [                        //카테고리
        "튜토리얼" 
    ],
    "tags": [],                            //태그
    "acceptComment": true,                 //댓글 설정(disqus)
    "acceptTrackback": true,               //트랙백 설정
    "published": "2012-05-14T04:33:48.267Z",    //공개된 날짜
    "status": "publish",                         //공개 상태 설정(publish or draft)
    "important": false,                         //중요 리본 설정
    "advanced": {}                              //기타 고급 설정
}

//여기부터는 내용 영역
...
```


#### 페이지
블로그 페이지 데이터는 포스팅과 동일하게 두가지로 분리됩니다.

```
{
  헤더
}

내용
```

##### 포스팅 기본 포맷
```js
{
    "title": "하루프레스 데이터 포맷 소개",    //블로그 제목
    "author": "Rhio kim",                  //작성자
    "date": "2012-05-14T04:33:48.267Z",    //작성 시간
    "categories": [                        //카테고리
        "튜토리얼" 
    ],
    "tags": [],                            //태그
    "acceptComment": true,                 //댓글 설정(disqus)
    "acceptTrackback": true,               //트랙백 설정
    "published": "2012-05-14T04:33:48.267Z",    //공개된 날짜
    "status": "publish",                         //공개 상태 설정(publish or draft)
    "important": false,                         //중요 리본 설정
    "advanced": {                               //기타 고급 설정
        "layout": "page"                        //
     }                              
}

//여기부터는 내용 영역
...
```

#### 작성자
작성자의 경우 포스팅이나 페이지의 헤더 영역의 저작자(author) 필드와 파일명이 매칭이 되기 때문에 파일명은 굉장히 중요합니다.

```js
{
 ...,
 "author": "Rhio kim",
 ...
}

내용
```

포스팅의 헤더가 다음과 같을때 파일명은 파일명 : `Rhio kim.markdown` 으로 다음과 같이 지정된 경로(`/path/to/haroopress/source/data/authors/Rhio kim.markdown`)에 작성자 markdown 이 존재해야 합니다.

```js
{
  헤더
}

내용
```

##### 포스팅 기본 포맷
```js
{
    "name": "작성자 이름",
    "blog": "http://haroopress.github.com",
    "twitter": "haroopress",
    "github": "haroopress",
    "vimeo": "haroopress",
    "youtube": "haroopress",
    "facebook": "haroopress",
    "linkedin": "",
    "email": "rhio.kim@gmail.com"
}

//여기부터는 소개 내용을 markdown 포맷으로 입력하세요.
# Header 1
헤더 1 내용

## Header 2
헤더 2 내용

[링크](http://haroopress.github.com)
...
```
