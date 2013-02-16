{
    "title": "하루프레스 확장 마크다운",
    "author": "Rhio Kim",
    "date": "2012-10-06T06:47:51.939Z",
    "categories": [
        "haroopress",
        "tutorial"
    ],
    "tags": [],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-11-17T06:47:51.939Z",
    "status": "publish",
    "important": false,
    "advanced": {}
}

#### Youtube

**markdown**
```markdown
[youtube:key [width] [height]]
```

**becomes**

[youtube:9bZkp7q19f0]

위와 같이 동영상을 첨부할 수 있게 된다. 현재까지는 조금 부족한 상태이다. 좀더 개선된 시점에 플러그인 기능은 별도의 글로 소개할 예정이다.

**width, height 값 설정**

```markdown
[youtube:MCEcWcIww5k 100% 215px]
[youtube:9bZkp7q19f0 516px]
[youtube:QlWZluzBNxM 300px 500px]
 ```

**becomes**

[youtube:MCEcWcIww5k 100% 215px]

[youtube:9bZkp7q19f0 516px]

[youtube:QlWZluzBNxM 300px 500px]
 
#### jsfiddle

**markdown**

```markdown
[jsfiddle:key]
[jsfiddle:key [tab] [skin] [height] [width]]
```

**becomes**

[jsfiddle:ccWP7]

**탭 지정**

[jsfiddle:ccWP7 result,js,html,css]

[jsfiddle:ccWP7 default presentation]

[jsfiddle:ccWP7 default presentation 300px 450px]

#### tweet

트위터의 사용이 잦아지면서 포스팅에 트위터 내용을 첨부하고 싶은 경우가 자주 있다.  하루프레스는 트윗 `237213915593965568` 형태의 트윗 코드만 알면된다. 
그리고 아래의 플러그인 코드를 이용해 포스팅에 트윗 내용을 첨부해보세요.

**markdown**

```markdown
[tweet:237213915593965568]
````

**becomes**

[tweet:237213915593965568]

**example**

```markdown
[tweet:237213915593965568]
[tweet:237213915593965568 center]
[tweet:237213915593965568 right]
```

**왼쪽 정렬**

[tweet:250113357066158080]

**가운데 정렬**

[tweet:266928743946268674 center]

**오른쪽 정렬**

[tweet:267593051986350080 right]

### gist
Github.com 의 gist 를 블로그 포스팅에서 포함시킬 수 있는 플러그인입니다.
* [https://gist.github.com/4094468](https://gist.github.com/4094468)

**markdown**

```markdown
[gist:4094468]
```

**become**

[gist:4094468]

### vimeo

**markdown**

**become**
[vimeo:53157569]

### pdf

**pdf**

**become**
[pdf:clock.co.uk/downloads/ten-reasons-to-use-nodejs.pdf]