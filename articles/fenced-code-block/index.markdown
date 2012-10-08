{
    "title": "구문 강조를 위한 펜스 코드 블럭(fenced code block)",
    "author": "Rhio Kim",
    "date": "2012-10-03T15:08:38.696Z",
    "categories": [
        "haroopress"
    ],
    "tags": [],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-10-03T15:08:38.696Z",
    "status": "draft",
    "important": false,
    "advanced": {}
}

언젠가부터 웹 페이지에 코드를 표현하고자 할 때 구문 강조 라이브러리를 사용하게 되었다.  최근 Github.com 이 주목을 받으며 마크다운(markdown) 포맷 문서화와 펜스 코드 블럭(fenced code block) 이 자주 활용되곤 한다.

특히 개발자 블로그에서는 필수 유틸이라고 할 수 있다.

하루프레스 0.9.0 버젼에서는 구문 강조를 위한 펜스 코드 블럭을 제공한다. 뿐만 아니라 코드블럭에 원하는 스타일을 적용할 수도 있다.

### 구문강조 라이브러리
구문 강조는 [highlight.js](http://softwaremaniacs.org/soft/highlight/en/) 를 이용했다.  [highlight.js](http://softwaremaniacs.org/soft/highlight/en/) 는 52 가지 언어를 지원하고 26가지의 유명한 구문 강조 스타일을 제공한다.


Language  | key
------------- | -------------
Python  | python
Python's profiler output | profile
Ruby  | ruby
Perl | perl
PHP | php
Scala | scala
Go | go
XML | xml
HTML (with inline css and javascript | xml
Markdown | markdown
Django templates | django
CSS | css
JSON | json
JavaScript | javascript
CoffeeScript | coffeescript
ActionScript | actionscript
VBScript | vbscript
HTTP | http
Lua | lua
Delphi | delphi
Java | java
C++ | cpp
Objective C | objectivec
Vala | vala
C# | cs
D | d
RenderMan RSL | rsl
RenderMan RIB | rib
MEL | mel
GLSL | glsl
SQL | sql
SmallTalk | smalltalk
Lisp | lisp
Clojure | clojure
Ini file | ini
Apache | apache
nginx | nginx
Diff | diff
DOS batch files | dos
Bash | bash
CMake | cmake
Axapta | axapta
1C | 1c
AVR Assembler | avrasm
VHDL | vhdl
Parser 3 | parser3
TeX | tex
Haskell | haskell
Erlang | erlang
Rust | rust
Matlab | matlab
R | r

### 구문강조 스타일 종류

Style | key
----- | -----
Default | **default**
Dark | **dark**
FAR | **far**
IDEA | **idea**
Sunburst | **sunburst**
Zenburn | **zenburn**
Visual Studio | **vs**
Ascetic | **ascetic**
Magula | **magula**
**GitHub** | **github**
Google Code | **googlecode**
Brown Paper | **brown_paper**
School Book | **school_book**
IR Black | **ir_black**
**Solarized - Dark** | **solarized_dark**
Solarized - Light | **solarized_light**
Arta | **arta**
Monokai | **monokai**
XCode | **xcode**
Pojoaque | **pojoaque**
Rainbow | **rainbow**
**Tomorrow** | **tomorrow**
Tomorrow Night | **tomorrow-night**
Tomorrow Night Bright | **tomorrow-night-bright**
Tomorrow Night Blue | **tomorrow-night-blue**
Tomorrow Night Eighties | **tomorrow-night-eighties**

컬러 테마로 잘 알려진 Solarized, Tomorrow 씨리즈는 기본으로 Github 스타일도 제공한다.  그외 위와 같이 굉장히 다양한 스타일을 제공한다.

좀더 자세한 스타일은 [여기](http://softwaremaniacs.org/media/soft/highlight/test.html)를 참고하세요.

## 적용 방법
하루프레스에서는 간단한 방법으로 코드블럭 스타일을 전역적으로 적용할 수 있을 뿐 아니라 각 페이지마다 별도의 디자인을 적용할 수 있다.

먼저 마크다운에서 코드 블럭을 지정하는 방법을 알아보도록 하자.

### 코드 블럭
마크다운에서 기본 코드 블럭은 1tab 혹은 4spaces 이다.  그런데 [Github.com](http://github.github.com/github-flavored-markdown/) 에서는 3개의 backtick <code>`</code> 을 연달아 작성하는 것으로 구문강조 코드 블럭을 지원하면서 이 **Fenced Code Block** 가 코드 블럭의 기본 방식처럼 되어가고 있다.

그외에 tilde <code>~</code> 3개를 이용해 코드 블럭을 지정하는 방법 중에 하나이다.

<pre><code class="markdown">```ruby
code block
```

~~~
fenced code block
~~~

~~~javascript
function syntaxhighlight(code, lang) {
   var foo = 'rhio';
   var bar = 33;
}
~~~
</code></pre>

### 기본 스타일
기본 스타일은 하루프레스 환경설정 파일에 설정하는 테마로 특별히 지정하지 않는 코드 블럭에는 환경설정에 지정한 스타일로 적용된다.

환경설정 파일은 하루프레스 설치 디렉토리에 `config.js` 파일에 존재한다. 이 파일을 JSON 포맷으로 이루어져있다.

코드 블럭 스타일을 지정은 `config.defaultCodeStyle` 이라는 값에 지정할 수 있다.  하루프레스 기본값은 `github` 으로 설정되어 있고 위의 스타일 목록에서 `key` 값을 참조하여 지정하면 된다.

### 페이지별 스타일
하루프레스는 기본 스타일뿐만 아니라 포스팅 별 코드 블럭에 스타일을 지정할 수가 있다. 하루프레스를 이용하고 있는 유저라면 별 어려움이 없게 간단한 옵션 하나로 지정할 수 있다.

포스팅한 마크다운 파일을 열어 [메타 정보](http://haroopress.com/post/haroopress-default-data-format/)의 JSON 포맷에 일부 옵션을 설정하면 된다.  

* 참고 : [하루프레스의 기본 데이터 규약](http://haroopress.com/post/haroopress-default-data-format/)

```javascript
{
  …,
  advanced : { }
}
```

위와 같이 기본적으로 `advanced:{}` 는 빈 객체가 지정되어 있는데 여기에 `codeStyle` 키에 값을 지정하면 된다.

```javascript
{
  …,
  advanced: {
    codeStyle: 'solraized_dark'
  }
}
```

## 요약
구문 강조는 개발자 블로깅에 Must Have 아이템이 아닐 수 없다.  50개가 넘는 언어 지원과 30개에 육박하는 다양한 스타일 테마로 블로그 테마에 어울리고 페이지 성격에 걸맞는 스타일을 사용자가 원하는 데로 적용할 수 있다.

하루프레스를 이용하며 발생하는 문제나 좋은 아이디어들은 직접 fork 해 구현해도 좋고 아래 이슈 트래커에 언제든지 남겨주세요.

* [하루프레스 이슈트래커](https://github.com/rhiokim/haroopress/issues)

## 함께 보세요.
* highlight.js : [http://softwaremaniacs.org/soft/highlight/en/](http://softwaremaniacs.org/soft/highlight/en/)
* marked : [http://markedapp.com/help/](http://markedapp.com/help/)
* Introduction to GFM : [http://github.github.com/github-flavored-markdown/](http://github.github.com/github-flavored-markdown/), [한글](http://dogfeet.github.com/articles/2012/dogfeet-flavored-markdown.html)
