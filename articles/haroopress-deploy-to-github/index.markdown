{
    "title": "블로그 깃허브(Github)로 배포하기",
    "author": "Rhio Kim",
    "date": "2012-05-26T03:45:12.315Z",
    "categories": [
        "tutorial"
    ],
    "tags": [],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-05-26T03:45:12.315Z",
    "status": "public",
    "important": true,
    "advanced": {}
}

## 배포 전 필수 설정사항
하루프레스로 작성된 블로그는 다른 블로그 엔진과는 다르게 로컬 PC 에서 작성되기 때문에 배포의 과정이 별도로 필요합니다. 하지만 그 과정이 복잡하거나 어렵지 않습니다.

### 깃허브(Github)에 저장소 생성하기
1. [github](http://github.com) 에 접속한다. 

2. 본인의 계정으로 로그인 한 후 새로운 저장소를 생성한다.
![github 저장소 생성 페이지](./@img/new-repository.png "저장소 생성 페이지")

3. `Repository name` 에는 본인의 github.com 계정 아이디를 입력합니다. 예시) '**rhiokim**.github.com'
4. `Description` 은 저장소를 설명을 간단히 작성하면 됩니다.  예시) **하루프레스 기반 리오의 자바스크립트 이야기**
![저장소 입력할 내용](./@img/set-repository.png "저장소 입력할 내용")


## 배포하기
```
$ cd /path/to/aaa.mysite.com
$ make gen
haroo> … 
haroo> generating log
haroo> …
$ make deploy
```