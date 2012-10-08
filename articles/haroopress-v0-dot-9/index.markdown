{
    "title": "하루프레스 v0.9 에서 준비중인 기능",
    "author": "Rhio Kim",
    "date": "2012-10-06T12:21:50.065Z",
    "categories": [
        "haroopress"
    ],
    "tags": [],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-10-06T12:21:50.065Z",
    "status": "publish",
    "important": false,
    "advanced": {}
}

***하루프레스 v0.9 에서 준비중인 따끈 따끈한 기능의 알려드립니다.***

## 전형적인 마크다운보다 개선된 점

표준 마크다운 문법보다 좀더 나은 문서 표현을 위해 확장된 문서 포맷으로 **멀티 마크다운** 이라는 포맷도 존재한다.

이 기능중 v0.9 에서는 테이블 기능과 자동 링크 그리고 펜스 코드 블럭(Fenced Code Block) 을 제공할 예정이다.

### 테이블 기능

**markdown**

```markdown
column | column
------ | ------
 row 1 | row1
 row 2 | row2
```

**becomes**

column | column
-------- | ---------
row1 | row1
row2 | row2

### URL 자동 링크
일반적으로 마크다운에서 링크는 `(link)[url]` 문법을 사용한다.  하지만 대부분의 마크다운 문서가 웹으로 퍼블리싱될 때에는 굳이 링크를 위해 마크다운 문법을 사용하는 것은 다소 번거러운 일이 될 수 있다. 이번 버젼에서 이부분을 개선한 자동 링크 기능을 추가하였다.

**markdown**

```markdown
* [http://haroopress.com](http://haroopress.com)
* http://haroopress.com
* https://github.com/rhiokim/haroopress
* mailto:abc123@gmail.com
```

**becomes**

* [http://haroopress.com](http://haroopress.com)
* http://haroopress.com
* https://github.com/rhiokim/haroopress
* mailto:abc123@gmail.com

### 펜스 코드블럭
펜스 코드 블럭은 [Github Flavored Markdown](http://github.github.com/github-flavored-markdown/) 으로 코드 구문 강조를 위한 확장 마크다운 문법중에 하나이다.

펜스 코드 블럭은 v0.9 이전 버젼에서도 지원하였지만 v0.9 버젼에서는 강력한 기능을 지원할 예정이다. 자세한 기능은 별도로 소개할 예정이다.

**markdown**
<pre><code class="markdown">```javascript
function syntaxHighlight() {
   var n = 33;
   var s = "hi";
   console.log(s);
}
```
</code></pre>

**becomes**

```javascript
function syntaxHighlight() {
   var n = 33;
   var s = "hi";
   console.log(s);
}
```

### 트리플 강조구문
트리플 강조 구문은 `<em><strong></strong></em>` 으로 일반 강조보다 더 강조를 하기 위한 문법이다.

하루프레스에서는 이 부분을 트위터 부트스트랩을 그대로 적용하였다. 문법은 다음과 같다.

**markdown**

<pre><code class="markdown">*** 강조 할 구문 ***</code></pre>

**becomes**

***강조 할 구문***

여기에서 끝난다면 별로 특별한 점이 없다.  그래서 몇가지 기능을 더 추가하였다.
트위터 부트스트랩에 보면 4가지 정도의 Alert 박스를 제공한다.  이 트리플 강조 문법을 사용하는 방법은 간단하다.

**markdown**

<pre><code class="markdown">***info 알림 성 강조 구문 ***
***error 경고 성 강조 구문***
***success 정보 성 강조 구문***</code></pre>

**becomes**

***info 알림성 강조 구문***
***error 경고성 강조 구문***
***success 정보성 강조 구문***

#### 함께보세요.
현재 하루프레스에 마크다운 모듈은 [robotskirt](https://github.com/benmills/robotskirt) 라는 모듈을 사용중이다. 이 모듈은 Github 에서도 채용중인 sundown 라이브러리를 사용해 작성된 노드 모듈이다.

