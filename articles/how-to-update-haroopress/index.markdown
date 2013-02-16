{
    "title": "how to update haroopress",
    "author": "Rhio Kim",
    "date": "2012-11-30T21:33:04.573Z",
    "categories": [
        "tutorial"
    ],
    "tags": [],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-11-30T21:33:04.573Z",
    "status": "draft",
    "important": false,
    "advanced": {}
}

## 하루프레스 업데이트

최초 하루프레스를 `git clone https://github.com/rhiokim/haroopress.git` 방식으로 설치하였다면 
하루프레스 업데이트는 생각보다 간단하다.

복제한 로컬 저장소에서 `make update` 를 입력하게 되면 자동으로 업데이트가 된다.

### make update 절차

1. git pull origin master
> haroopress 원격 저장소에서 최신의 소스를 내려 받는다.
2. npm
