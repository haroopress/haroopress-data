{
    "title": "하루프레스 컨텐츠 퍼블리싱 가이드",
    "author": "Rhio Kim",
    "date": "2012-07-08T03:33:26.870Z",
    "categories": [
        "tutorial"
    ],
    "tags": [],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-07-08T03:33:26.870Z",
    "status": "public",
    "important": false,
    "advanced": {}
}

글을 모두 작성했다면 이제 누군가가 내가 작성한 글을 볼 수 있도록 해야합니다.  하지만 하루프레스는 웹 서버없이 내 컴퓨터에서 돌아가고 있기 때문에 누군가 보려면 어딘가에 업로드를 해야합니다. (리오 : rsync 를 이용한 원격지 서버 배포도 지원 예정)

혹 자신이 가지고 있는 웹 서버가 있다면 웹 서버에 올려도 좋습니다.  하지만 웹 서버도 없고 도메인 연결도 번거롭다면 [Github Pages](https://help.github.com/articles/what-are-github-pages) 기능을 이용해보는 것도 좋습니다.

## Github Pages 란?

>Github Pages are public webpages freely hosted and easily published through our site. You can publish online using the Automatic Page Generator. If you prefer to work locally you can use the GitHub for Mac and Windows apps, or the command line.

Github 는 어마어마한 오픈소스 프로젝트가 진행되는 소셜 코딩 허브입니다.  Github 는 이런 오픈 소스 프로젝트가 프로젝트에 집중할 수 있도록 편리한 기능들을 많이 제공하고 있습니다. 

그중에 하나! 프로젝트를 소개할 웹 페이지 구축을 자동화해주는 기능을 가지고 있습니다. 그게 Github Pages 입니다. 이는 정적인 웹 페이지 방식으로 특정 브랜치에 웹 페이지를 디자인해서 올리면 그 페이지가 특정 URL(계정.github.com/index.html) 로 자동으로 서비스되게 됩니다.

하루프레스도 바로 이 기능을 이용하여 웹 서버없이 본인이 가지고 있는 콘텐츠를 블로그로 서비스할 수 있게 해주는 블로그 엔진입니다.

개발자가 아니라면 Github 의 사용에 다소 어려움을 느낄 수 있으나 

## Github 계정 생성

## Github 저장소 생성

## 하루프레스 배포