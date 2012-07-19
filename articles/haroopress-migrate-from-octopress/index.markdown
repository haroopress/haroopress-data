{
    "title": "옥토프레스 데이터 마이그레이션",
    "author": "Rhio Kim",
    "date": "Wed Jul 18 2012 18:03:48 GMT+0900 (KST)",
    "categories": [
        "tutorial"
    ],
    "tags": [],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "Wed Jul 18 2012 18:03:48 GMT+0900 (KST)",
    "status": "public",
    "important": false,
    "advanced": {}
}

하루프레스는 향후 유명한 몇가지 블로그 엔진 데이터를 마이그레이션할 수 있도록 할 예정입니다.  
구현 가능성을 판단하기 위해서 하루프레스의 유사품인 [옥토프레스](http://octopress.org) 마이그레이션 기능이 탑재되어있습니다.

![](./@img/octopress.png)

하루프레스의 대부분의 명령은 콘솔상에서 동작하도록 디자인되어 있다는 것을 알고 있으면 편리하게 이용할 수 있습니다. 어떤 기능들이 숨어있는지 보려면 `Makefile` 을 참고하시는 것도 좋습니다.

## 기본 명령
가장 중요한 명령어는 `make octopress` 입니다. 

```
$ make octopress
========================================
= convert from octopress
========================================
cd ./bin/convert/;./octopress.js

Please! insert octopress article directory : <strong>{octopress article directory}</strong>
```

### 옥토프레스 콘텐츠 폴더 지정하기

명령어를 수행하면 옥토프레스의 콘텐츠 위치를 입력해 주어야 합니다.
옥토프레스의 데이터는 기본적으로 `source/_post/*.markdown` 에 존재하기 때문에 절대 경로를 지정해주시면 됩니다.

결과적으로 `옥토프레스/source/_post/` 에 존재하는 모든 markdown 파일을 `하루프레스/source/data/articles` 디렉토리로 마이그레이션 됩니다.

실행결과

```
Please! insert octopress article directory : /path/to/octopress/source/_posts
…

haroo> create directory at /Users/rhio/Works/sites/myblog.com/source/data/articles/포스팅_제목
haroo> create image directory at /Users/rhio/Works/sites/myblog.com/source/data/articles/포스팅_제목/@img
haroo> copy to 포스팅_제목.markdown file
----------------------------------------------------------------
…
haroo> jekyll convert to haroopress
```

위와 같이 옥토프레스 데이터를 마이그레이션을 진행합니다.   `jekyll convert to haroopress` 메세지가 표시되면 정상적으로 완료된 것입니다.

## 동영상

<iframe src="http://player.vimeo.com/video/45813575?color=ffffff" width="100%" height="550" frameborder="0" webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe> <p><a href="http://vimeo.com/45813575">haroopress deploy guide</a> from <a href="http://vimeo.com/rhio">rhiokim</a> on <a href="http://vimeo.com">Vimeo</a>.</p>