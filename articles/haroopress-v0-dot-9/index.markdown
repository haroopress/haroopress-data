{
    "title": "하루프레스 v0.9 를 소개합니다.",
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
    "important": true,
    "advanced": {
        "codeStyle": "rainbow"
    }
}

새로운 기능 소개에서는 ***warning Experimental: 1***, ***success  Stablity: 3*** 으로 나뉘어 설명할 예정입니다.  ***success 안정*** 상태인 기능은 변경이 없는 안정화된 버젼을 가리키며 ***warning 실험*** 상태의 기능은 다소 변경될 수 있는 기능을 의미합니다.

## 전형적인 마크다운보다 개선된 점

>***success Stability: 3 - Stable***

표준 마크다운 문법보다 좀더 나은 문서 표현을 위해 확장된 문서 포맷으로 **멀티 마크다운** 이라는 문법도 존재한다.

v0.9 에서는 멀티 마크다운의 일부 인 **테이블 기능**, **자동 링크**, **펜스 코드 블럭**(Fenced Code Block) 그리고 **강조구문**(Triple Emphasis) 을 제공할 예정이다.

그리고 커스텀 문법을 이용한 **플러그인 기능**을 추가 할 예정입니다.

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

> ***success Stability: 3 - Stable***

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

> ***success Stability: 3 - Stable***

펜스 코드 블럭은 [Github Flavored Markdown](http://github.github.com/github-flavored-markdown/) 으로 코드 구문 강조를 위한 확장 마크다운 문법중에 하나이다.

펜스 코드 블럭은 v0.9 이전 버젼에서도 지원하였지만 v0.9 버젼에서는 강력한 기능을 추가 지원할 계획이다.  자세한 기능은 별도의 포스팅으로 소개할 예정이다.

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

> ***success Stability: 3 - Stable***
> 
> ***important <i class="icon-info-sign icon-white"></i> 트리플 강조 구문은 처음 박스 형태로 제공하려 하였으나 표준에 어긋나 본래의 형태로 처리함.  2012.10.11 변경***

트리플 강조 구문은 `<em><strong></strong></em>` 으로 일반 강조보다 더 강조를 하기 위한 문법이다.

하루프레스에서는 트리플 강조 구문의 스타일을 트위터 부트스트랩의 라벨 스타일을 적용하였다. 문법은 다음과 같다.

**markdown**

<pre><code class="markdown">*** 강조 할 구문 ***</code></pre>

**becomes**

***강조 할 구문***

강조 형태는 총 6가지 이다.

트위터 부트스트랩에 보면 6가지 라벨 스타일을 제공한다.   트리플 강조 문법에 스타일을 선택하는 문법은 다음과 같다.

**markdown**

<pre><code class="markdown">***기본 강조***
***info info 강조 구문 ***
***warning warning 강조 구문***
***success success 강조 구문***
***important important 강조 구문***
***inverse inverse 강조 구문***</code></pre>

**becomes**

***기본 강조***
***info info 강조 구문***
***warning warning 강조 구문***
***success success 강조 구문***
***important important 강조 구문***
***inverse inverse 강조 구문***


추가적인 팁을 드리자면 부트스트랩에서 제공되는 아이콘을 함께 사용할 수도 있다.

**markdown**

<pre><code class="markdown">***info &lt;i class="icon-info-sign icon-white"&gt;&lt;/i> info 강조 구문***
***warning &lt;i class="icon-warning-sign"&gt;&lt;/i&gt; warning 강조 구문***
***success &lt;i class="icon-ok-sign"&gt;&lt;/i&gt; success 강조 구문***
***important &lt;i class="icon-flag">&lt;/i&gt; important 강조 구문***
***inverse &lt;i class="icon-refresh"&gt;&lt;/i&gt; inverse 강조 구문***
</code></pre>

**becomes**

***<i class="icon-flag icon-white"></i> 기본 강조 구문***
***info <i class="icon-info-sign icon-white"></i> info 강조 구문***
***warning <i class="icon-warning-sign"></i> warning 강조 구문***
***success <i class="icon-ok-sign"></i> success 강조 구문***
***important <i class="icon-bookmark"></i> important 강조 구문***
***inverse <i class="icon-refresh"></i> inverse 강조 구문***

**example**

> ***info <i class="icon-info-sign icon-white"></i> 참고사항*** 글을 작성하다보면 다양한 형태의 강조 형식을 사용하게 된다. 그런데 대부분 볼드처리를 하거나 밑줄을 긋거나 색상을 바꿔 처리하는 것이 대부분이다. 물론 그런 방법도 있지만 하루프레스에서는 간단한 ***inverse <i class="icon-refresh"></i> 강조 문법***을 제공하여 좀더 독자가 좀더 쉽고 적절하게 인지할 수 있게 한다.
> ***success <i class="icon-ok-sign"></i> 필독사항*** 꼭 읽어야 할 내용에는 ***success 필독*** 마크를 추가하고 싶어지기도 하다.
>
> ***important 중요사항*** 새로 업데이트 된 내용이 있어서 꼭 알리고 싶은 내용이 있을 때는 ***important 중요*** 마크를 추가할 수도 있다.
> 
> ***warning <i class="icon-warning-sign"></i> 경고성 문구에 강조하는 방법은 warning 을 사용한다.*** 
 
* 트위터 부트스트랩 아이콘 : [http://twitter.github.com/bootstrap/base-css.html#icons](http://twitter.github.com/bootstrap/base-css.html#icons)

## 플러그인을 위한 커스텀 문법

> ***warning Stability: 3 - Experimental***
>
> ***important 이 기능은 현재 구현 및 테스트 중입니다. 그래서 커스텀 문법의 구조가 언제든지 변경될 수 있다는 점 참고바랍니다.***

전형적인 마크다운만으로는 복잡한 문서 표현의 한계가 있다. 그래서 멀티 마크다운을 통해 좀더 복잡한 문서 구조를 표현할 수 있게 되었고 여기에 더불어 복잡한 미디어 컨텐츠와 오픈 컨텐츠를 웹 페이지에 표현하기 위한 커스텀 문법을 제공한다.

하루프레스도 마크다운을 기반으로 오픈된 웹 컨텐츠들을 문서에 손쉽게 첨부할 수 있도록 커스텀 문법을 제공하려 연구중에 있다.

작성하고 있는 마크다운 문서에 유투브 동영상을 첨부하고 싶은 사용자에게는 다음과 같은 문법을 사용하면 된다.

#### Youtube
**markdown**
<pre><code class="markdown">[youtube:9bZkp7q19f0]</code></pre>

**becomes**

[youtube:9bZkp7q19f0]

위와 같이 동영상을 첨부할 수 있게 된다. 현재까지는 조금 부족한 상태이다. 좀더 개선된 시점에 플러그인 기능은 별도의 글로 소개할 예정이다.
 
#### jsfiddle

**markdown**
<pre><code class="markdown">[jsfiddle:ccWP7]</code></pre>

**becomes**

[jsfiddle:ccWP7]

#### tweet

트위터의 사용이 잦아지면서 포스팅에 트위터 내용을 첨부하고 싶은 경우가 자주 있다.  하루프레스는 트윗 `237213915593965568` 형태의 트윗 코드만 알면된다. 
그리고 아래의 플러그인 코드를 이용해 포스팅에 트윗 내용을 첨부해보세요.

**markdown**
<pre><code class="markdown">[tweet:237213915593965568]</code></pre>

**becomes**

[tweet:237213915593965568]

**example**

<pre><code class="markdown">[tweet:237213915593965568]
[tweet:237213915593965568 center]
[tweet:237213915593965568 right]
</code></pre>

**left**

[tweet:237213915593965568]

**center**

[tweet:237213915593965568 center]

**right**

[tweet:237213915593965568 right]

### 플러그인 옵션
현재 위의 두가지 플러그인만 v0.9.0 버젼에서 제공될 예정이고 v0.9.x 버젼동안 다음과 같은 플러그인들을 추가로 제공할 예정이다.

* vimeo
* gist
* map

물론 사용자 피드백도 수렴할 것이고 [여기](https://github.com/rhiokim/haroopress/issues/245) 에 코멘트로 제안하면 된다.