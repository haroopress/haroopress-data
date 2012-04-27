{
    "title": "하루프레스 포스팅하기",
    "author": "Rhio Kim",
    "date": "2012-04-25T16:09:23.234Z",
    "categories": [
        "tutorial",
        "haroopress"
    ],
    "tags": [],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-04-25T16:09:23.234Z",
    "status": "public",
    "important": false,
    "advanced": {}
}

## 포스팅하는 방법
하루프레스는 전용 CLI(Command-Line Interface) 명령줄 도구를 포함하고 있습니다.  새로운 기사를 작성하거나 페이지를 추가할 때 이 명령어를 사용하게 됩니다.

#### 새로운 기사를 작성

```
$ haroo post
haroo> insert article title : [포스팅 제목] 
haroo> insert article\'s categories (e.g. cate1, cate2, cate3) : 카테고리1, 카테고리2
haroo> insert article\'s tags (e.g. tag1, cate2, cate3) : 태그1, 태그2
Article Path : /User/path/to/haroopress/source/data/articles/[포스팅 제목]/index.markdown
Article\'s Image Path : /User/path/to/haroopress/source/data/articles/@img
```

#### 새로운 페이지를 작성

```
$ haroo page
haroo> insert article title : [페이지 제목] 
haroo> insert article\'s categories (e.g. cate1, cate2, cate3) : 카테고리1, 카테고리2
haroo> insert article\'s tags (e.g. tag1, cate2, cate3) : 태그1, 태그2
Article Path : /User/path/to/haroopress/source/data/articles/[페이지 제목]/index.markdown
Article\'s Image Path : /User/path/to/haroopress/source/data/articles/@img
```

## 포스팅 확인하기
글을 모두 작성했다면 하루프레스에 적용된 페이지를 배포하기 전에 미리 보고 싶을 것입니다.  미리 보기를 하기 전에 작성된 글들을 정적 페이지로 생성해야 합니다.

### 정적 페이지 생성

```
$ haroo gen
```

위와 같이 할 경우 작성된 모든 글을 정적 페이지로 생성합니다. 

### 미리보기

그리고 바로 `haroo preview` 명령을 수행하면 로컬 웹 서버가 자동으로 구동되면서 하루프레스가 적용된 정적 웹 페이지를 브라우저에서 확인할 수 있습니다.

```
$ haroo preview
```
