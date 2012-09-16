{
    "title": "하루프레스 개발 로드맵",
    "author": "Rhio Kim",
    "date": "2012-04-26T10:59:35.972Z",
    "categories": [
        "haroopress"
    ],
    "tags": [],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-04-26T10:59:35.972Z",
    "status": "publish",
    "important": false,
    "advanced": {}
}

하루프레스 블로그의 로드맵을 소개합니다.

## v0.0.1
하루프레스의 가장 중요한 것은 마크다운 포맷으로 포스팅을 할 수 있는 것과 정적 페이지를 생성하는 엔진이였습니다.  그래서 `v0.0.1` 버젼에서는 이에 필요한 기본 뼈대를 디자인하는 것에 목적을 두었습니다.

* markdown article module
* default blog structure

## v0.1.0
`v0.1.0` 버젼에서는 기본 뼈대에 더해질 플러그인의 구조를 설계하였습니다.  다양한 플러그인 들중에 댓글 시스템을 제공하는 disqus.com 플러그인을 제작하였고 소셜라이징을 위한 Facebook Like 버튼을 플러그인화 하였습니다.

* plugin structure
 - disqus
 - facebook like button

## v0.2.0
`v0.2.0` 에서는 rss, atom 을 제공하기 위한 기능을 구현하였습니다.
 - support feed.xml

## v0.3.0
이 버젼에서는 기사를 성격에 맞게 분리하여 표시할 수 있는 구조를 설계하여 구현하였습니다.

* categorize
* tags
* date

## v0.4.0
하루 프레스의 주된 기능인 정적 페이지 렌더링은 ejs 템플릿 엔진으로 되어있고 노드의 파일 시스템 API 를 이용해 정적 페이지를 생성합니다.

 - static generator

## v0.5.0
하루프레서는 기본적으로 Github 의 정적 페이지 서비스에 포커싱되어 구현되었습니다.  `v0.5.0` 에서는 Github 에 손쉽게 퍼블리싱 할 수 있도록 자동화합니다.

 - gh-page auto publisher module

## v0.5.1 (hackathon issue)
`v0.5.1` 은 FRENDS Hackathon 2012 에 참가하면서 구현한 기능들로 Make 스크립트를 작성하여 터미널에서 하루프레스를 좀더 쉽게 사용할 수 있는 도구들을 개발하였습니다.

 - <del>git clone</del>
 - <del>make init ( submodule update & build, create _deploy dir )</del>
 - <del>update config.js ( setting custom information )</del>
 - <del>make github-page ( deploy setup to github.com gh-pages branch )</del>
 - <del>make gen ( generating static page )</del>
 - <del>make preview ( node app.js )</del>
 - make deploy ( git add . && git commit -m 'new Date()' && git push origin )

## v0.6.0
`v0.2.0` 에서 구현한 플러그인 구조에 좀더 다양한 플러그인들을 구현해 하루프레스에 포함시켰습니다.

* support other plugins
 - <del>google statics</del>
 - twitter button
 - twitter timeline
 - google plus +1 button
 - github repo list

## v0.7.0
이 버젼에서는 블로그가 아닌 페이지 단위의 블로그를 작성하기 위해 만들어졌습니다.

* page generator
* <del>sharethis.com plugin : http://sharethis.com/</del>

## v0.8.0
`v0.8.0` 에서는 굉장히 많은 이슈들을 처리하였고 테마 기능을 위한 구조 설게 및 구현을 하였습니다.

* theme

### v0.8.1
이 버젼에서는 CLI 를 Make 스크립트에서 노드로 컨버팅합니다. 이는 크로스 플랫폼에서 동일한 CLI 를 사용할 수 있도록 하기 위한 준비 단계입니다.

#### v0.8.2
이 버젼에서는

## v0.9.0
* cloud

## v0.10.0
* text, photo, video, audio

## v0.11.0
* documentation

## v1.0.0

## backlog
백 로그에는 하루프레스에 추가될 다양한 아이디어나 중요도와 우선순위를 지정하기 어려운 작업과 이슈들을 관리합니다.

* {stats: draft} documents publish manager
* admin tools