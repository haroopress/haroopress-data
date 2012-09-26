{
    "title": "make to jake",
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
    "status": "publish",
    "important": false,
    "advanced": {}
}

jake

## Make 란

## Jake 란

## Jake 로 전환한 이유
첫번째 이유는 윈도우 지원을 위해서입니다.  윈도우에서는 Make 유틸이 존재하지 않고 대부분 설치형 애플리케이션을 클릭으로 설치하기 때문에 커멘트 창에서 작업하는 경우는 거의 없습니다.

그렇다 보니 하루프레스와 같이 콘솔 명령에 의해서 동작하는 애플리케이션들은 

## Jake 로 전환하면서
하루프레스는 빌드 스크립트마저 노드를 기반으로 구현되었습니다. 그러다보니 시스템 파일을 접근하거나 자식 프로세스에 의존하는 경우도 많습니다.

이 이야기는 노드의 가장 주요 특징인 비동기 I/O 가 어마어마 하다는 이야기입니다.

파일의 존재 유무, 자동으로 Git 저장소를 초기화하고 커밋을 자동화하고 파일을 복사하고 삭제하는 일이 비일비재합니다.

그렇다보니 Make 와 같이 비동기에 대한 고민을 할 필요 없는 도구에서는 경험하지 못한 다양한 오류에 적잖은 시간을 소비하게 되었습니다.

### 비동기 Task 에 대한 처리
특히 비동기 `task` 처리 시  `{ async: true }` 옵션을 꼭 지정하여야 하고 비동기 `task` 간의 의존성이 있는 경우 `complete()` 메소드를 호출하며 비동기 `task` 가 종료되는 시점을 명확히 Jake 에 알려주어야 합니다.

> example
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

> example
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


> example
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

> example
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

## 함께 보세요.
* [http://nodeqa.com/nodejs_ref/12](http://nodeqa.com/nodejs_ref/12)
* [http://nodeqa.com/nodejs_ref/13](http://nodeqa.com/nodejs_ref/13)