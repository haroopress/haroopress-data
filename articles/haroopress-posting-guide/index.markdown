{
    "title": "하루프레스 포스팅 가이드",
    "author": "Rhio Kim",
    "date": "2012-06-22T08:38:28.284Z",
    "categories": [
        "tutorial"
    ],
    "tags": [],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-06-22T08:38:28.284Z",
    "status": "publish",
    "important": true,
    "advanced": {}
}

하루프레스 메인 소개 페이지에서도 확인할 수 있지만 하루프레스를 설치했다면 블로깅 하는 것은 식은 죽 먹기, 길 가다가 침 밷기, 손가락으로 코 후비기 만큼 쉬운일이 아닐 수 없다.

**이 명령어 하나만 기억하자.** 

```
$ make new-post
```

## 포스팅 시작 전 
콘솔에서 `make new-post` 명령을 실행하면 하루프레스는 다음과 같이 **제목**, **카테고리**, **태그** 세가지 정보를 입력해야 합니다.

```
$ make new-post
haroo> Input article title : 제목 ¶
haroo> Input article category : 카테고리 ¶
haroo> Input article tag (e.g tag1, tag2, tag3) : 태그 ¶
...
```

입력을 완료하고 나면 아래와 같이 `index.markdown` 파일과 `@img` 디렉토리가 지정된 위치에 생성됩니다.

```
haroo> write post -> /Users/{사용자계정}/path/to/{myblog.com}/source/data/articles/haroopress-posting-guide/index.markdown
haroo> article's image path /Users/{사용자계정}/path/to/{myblog.com}/source/data/articles/haroopress-posting-guide/@img
```


`index.markdown` 파일는 포스팅을 위한 파일로 내용을 입력하는 파일입니다.  

해당 `index.markdown` 파일을 에디터로 열어보면 다음과 같이 내용이 이미 채워져 있습니다.

```
//이 영역은 JSON 포맷은 변경하지 않고 필요에 따라 값만 수정합니다.
{
    "title": "{제목}",
    "author": "{작성자 닉네임}",
    "date": "2012-06-22T08:38:28.284Z",
    "categories": [
        "tutorial"
    ],
     ...
}

write here!   <-- 위 한줄을 띄우고 여기서부터 내용을 작성합니다. (write here 는 삭제)
```  

그리고 @img 는 포스팅에 포함될 이미지가 있다면 해당 이미지를 저장할 위치입니다.
만약 `index.markdown` 포스팅에 `logo.png` 파일이 포함된다면 `logo.png` 파일을 @img 디렉토리에 복사하고 블로그 본문에서는 상대경로로 지정하면 됩니다.

index.markdown 내용 예시

```
{ 
   헤더
}

# 하루프레스

## 이미지
![로고 이미지](./@img/logo.png)

```

## 동영상 가이드

위의 설명이 어렵다면 다음의 동영상을 보고 천천히 따라해보세요.  그래도 어렵다면 저에게(리오) 메일을 띄우거나 댓글로 남겨주시면 되겠죠?

<iframe src="http://player.vimeo.com/video/45558225?color=ffffff" width="100%" height="550" frameborder="0" webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe> <p><a href="http://vimeo.com/45558225">haroopress posting guide</a> from <a href="http://vimeo.com/rhio">rhiokim</a> on <a href="http://vimeo.com">Vimeo</a>.</p>