{
    "title": "Make 에서 Jake 로 전환하며",
    "author": "Rhio Kim",
    "date": "2012-09-26T16:14:49.877Z",
    "categories": [
        "diary"
    ],
    "tags": [
        "jake",
        "make"
    ],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-09-26T16:14:49.877Z",
    "status": "draft",
    "important": false,
    "advanced": {}
}

크로스 플랫폼의 정적 페이지 기반 블로깅 엔진 하루프레스를 개발하면서 크로스 플랫폼 빌드 스크립트 적용 경험 사례를 소개합니다.   주제는 Make 와 유사한 노드 기반의 Jake 입니다.

## Make
![image](@img/make01.png)

>Make 는 유닉스 계열 운영체제에서 소프트웨어 개발에 주로 사용되는 프로그램 빌드 도구입니다.
>
>여러 파일들끼리의 의존성과 각 파일에 필요한 명령을 정의함으로써 프로그램을 컴파일할 수 있으며 최종 프로그램을 만들 수 있는 과정을 서술할 수 있는 표준적인 문법을 가지고 있다.
위의 구조로 기술된 파일(주로 Makefile이라는 파일명)을 Make가 해석하여 프로그램 빌드를 수행하게 된다. via [wikipedia](http://ko.wikipedia.org/wiki/Make_(%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4)

## What's Jake
Jake 는 Make 닮은 꼴로 노드를 기반으로 하는 프로그램 빌드 스크립트를 위한 유틸입니다.  Jake 에는 Make 와 몇가지 다른 특징을 가지고 있습니다. 

* 자바스크립트 문법을 사용
* 의존성 타스크
* 타스크 네임스페이싱을 지원(그룹핑 및 호출 포인트)
* 비동기 타스크 지원

### Jake 레퍼런스
* [Intro to Jake](http://howtonode.org/intro-to-jake)
* [Official references](https://github.com/mde/jake/blob/master/README.md)

## Why Jake 
하루프레스는 본래 Mac OS 에서 개발되어 쉘을 기반으로 하는 처리는 모두 Make 에 의존하고 있습니다. 그래서 아무리 노드를 기반으로 구현되어져 있더라도 크로스 플랫폼의 이점을 얻을 수 없었으나 Make 와 유사한 모듈이 없나 고민하던 중 **Jake** 를 찾게 되었고 윈도우, 리눅스 할것 없이 모든 플랫폼에서 Make 와 유사한 처리를 하는데 무리가 없게 되었습니다.

## HarooPress Jake

하루프레스는 모두 자바스크립트로 구현되었는데 더불어 빌드 스크립트마저 노드를 기반으로 구현되었습니다.  이것은 파일 시스템을 접근하거나 네트워크를 통해 파일을 요청하거나 Git 저장소의 상태를 체크하거나 원격 저장소로 pull/push 를 하기도 합니다.

파일의 존재 유무, 자동으로 Git 저장소를 초기화하고 커밋을 자동화하고 파일을 복사하고 삭제하는 일이 비일비재합니다.

그렇다보니 Make 와 같이 비동기에 대한 고민을 할 필요 없는 도구에서는 경험하지 못한 다양한 오류에 적잖은 시간을 소비하게 되었습니다.

### Asynchronous task in Jake
![image](./@img/async.gif)

특히 비동기 `task` 처리 시  `{ async: true }` 옵션을 꼭 지정하여야 하고 비동기 `task` 간의 의존성이 있는 경우 `complete()` 메소드를 호출하며 비동기 `task` 가 종료되는 시점을 명확히 Jake 에 알려주어야 합니다.

> #### example
> 
> ```
> desc('타스크에 대한 설명');
> task('타스크 고유 아이디', { async: true }, function() {
>    var fs = require('fs');
>        fs.readFile('파일명', 'utf8', function(err, data) {
>            console.log(data);
>            complete();
>        });
> });
> ```

위의 예시와 같이 `파일명`의 파일을 읽어들이는데 비동기가 발생합니다. 
좀더 이해하기 쉬운 예시를 통해 살펴보기로 합니다.

> #### example
>
> ```
> task('타스크 고유 아이디', [ '다음 타스크' ], function() {
>     var fs = require('fs');
>     console.log(1);
>     fs.readFile('파일명', 'utf8', function(err, data) {
>         console.log(2);
>     });
>     console.log(3);
> });
>
> task('다음 타스크', function() {
>    console.log(4);
> });
> ```

위의 Jakefile 을 실행 결과를 예측해보면 절차적 수행에 비춰보면 `1 -> 2 -> 3 -> 4` 라고 생각할 수 있으나 Jake 에서는 `2, 3, 4` 의 순서를 원하는 데로 보장 받을 수 없습니다.

그렇기 때문에 async 옵션을 통해서 절차적으로 수행하도록 강제합니다. 


> #### example
>
> ```
> task('타스크 고유 아이디', [ '다음 타스크' ], { async: true }, function() {
>     var fs = require('fs');
>     console.log(1);
>     fs.readFile('파일명', 'utf8', function(err, data) {
>         console.log(2);
>         complete();
>     });
>     console.log(3);
> });
>
> task('다음 타스크', function() {
>    console.log(4);
> });
> ```

이렇게 위와 같이 `complete()` 를 추가하면 `1 -> 3 -> 2 -> 4` 순으로 수행됩니다.  사실 여기서도 약간 이상합니다. `3` 과 `2` 의 순서도 이상합니다.

이 부분도 `fs.readFile` 의 수행이 비동기이기 때문입니다.  이 코드 역시 의도적인 코드가 아닌 절차적 진행이 필요하다면 `console.log(3)` 코드의 위치가 `console.log(2)` 뒤로 이동해야 합니다.

> #### example
>
> ```
> task('타스크 고유 아이디', [ '다음 타스크' ], { async: true }, function() {
>     var fs = require('fs');
>     console.log(1);
>     fs.readFile('파일명', 'utf8', function(err, data) {
>         console.log(2);
>         console.log(3);
>         complete();
>     });
> });
>
> task('다음 타스크', function() {
>    console.log(4);
> });
> ```

와 같이 개선함으로써 `1 -> 2 -> 3 -> 4` 순서로 Jake `task` 가 수행될 수 있습니다.

## 요약
노드를 기반으로 한 Jake 는 Make 의 대체제로 더 없이 편리하고 크로스 플랫폼 지원을 고민할 필요가 없게 해주었습니다. 

하지만 Make 는 절차적 수행이라는 다소 쉬운 프로그래밍이 가능한 반면 Jake 의 경우 노드의 특징인 비동기 I/O 에 의해서 프로그래밍의 복잡도가 다소 복잡해짐은 사실입니다. 특히 Jake 에 의해 처리되는 복잡한 빌드 스크립트의 경우 Control Flow 모듈을 잘 활용하여 절차적 수행을 보장하는 것이 굉장히 중요하다는 것을 알게 되었습니다.

## 함께 보세요.
* [http://nodeqa.com/nodejs_ref/12](http://nodeqa.com/nodejs_ref/12)
* [http://nodeqa.com/nodejs_ref/13](http://nodeqa.com/nodejs_ref/13)