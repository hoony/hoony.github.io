---
layout: post
published: true
description: ""
headline: ""
modified: "2014-11-13"
categories: 
  - 춘식이의 코드이야기
tags: "스크레이핑, 자바스크립트, scraping, request, cheerio, javascript"
imagefeature: ""
mathjax: false
featured: false
comments: true
title: "[춘식이의 코드이야기] 10분만에 따라하는 웹사이트 긁어오기"
---

데이터를 활용하여 유용한 서비스 및 어플리케이션을 만드는 사례들이 늘어가고 있다. 이 때 원하는 공공데이터 혹은 일반 오픈 데이터를 찾지 못하는 경우 웹사이트를 그대로 가져와서 직접 처리하는 경우를 많이 볼 수 있다. 이런 방법을 크롤링(Crawling) 혹은 스크래이핑(Scraping)이라고 한다. 아마 크롤링이나 크롤러는 많이 들어보셨을 듯! 대표적으로 [팀포퐁](http://popong.com/)에서는 직접 [파이썬을 이용한 크롤러](https://github.com/teampopong/crawlers)를 만들어서 각종 정치 데이터를 가공한다. 가공한 데이터를 API 형태로 공개도 하고있다. 팀포퐁의 강철님께서는 파이썬 코리아 컨퍼런스 행사에서 ‘[30분만에 따라하는 동시성 스크래이퍼](https://gist.github.com/cornchz/0ec0c3f5ca69bac2b625)‘라는 주제로 발표한 적도 있다.

30분만에 동시성 스크래이퍼를 따라한다면 단순한 스크래이핑은 10분만에 가능하지 않을까? 꼭 스크래이핑은 파이썬으로만 해야할까? 그래서 준비했다. 자바스크립트를 활용한 ’10만에 따라하는 HTML 긁어오기’. 굳이 10분만에 따라할 수 있는 것은 HTML을 가져오기 위한 가장 기본적인 기능만을 만들어볼 것이다. 그리고 숙련된 개발자보다 이제 웹개발에 관심을 갖게된 분들에게 스크래이핑을 소개하는 차원에서 쓰는 예제이다. 마지막으로 개발자들이 자꾸 크롤러, 스크래이퍼 거릴 때 답답해하던 기획자와 디자이너 분들을 위해 기본적인 원리를 이해할 수 있도록 준비해보았다.

## 필요한 도구: [request](https://github.com/request/request), [cheerio](https://github.com/cheeriojs/cheerio)
`request`는 우리가 브라우저에서 주소창에 원하는 주소를 치고 홈페이지를 들어가듯, 원하는 웹사이트의 html을 불러와주는 도구이다. `cheerio`는 핵심 기능만 간단히 설명하면 HTML은 구조적인 태그들의 집합으로 볼 수 있는데 이 때 원하는 요소(태그 혹은 속성)에 쉽게 접근할 수 있도록 도와주는 도구이다<del>(이번 예제에서는 DOM에 대한 자세한 이야기는 생략)</del>. 핵심 내용은 `request`를 이용해서 내가 긁어오길 원하는 페이지의 URL을 이용하여 HTML 소스를 불러온 다음 `cheerio`를 이용하여 원하는 데이터를 가공하는 방식이다. 이번 예제에서는 [코드나무 블로그](http://codenamu.org/blog) 페이지를 불러와서 각 글마다 정리된 ‘제목’, ‘포스트주소’, ‘요약 내용’, ‘카테고리’ 세 가지 요소를 불러와본다.

## `request`를 이용하여 HTML 가져오기

<iframe src="http://jsfiddle.net/thechunsik/tdz8ukdg/2/embedded/" allowfullscreen="allowfullscreen" frameborder="0" height="265" width="100%"></iframe>

코드나무 블로그 HTML을 불러와서 변수 `$`에 `cheerio`를 이용해 담았다.

`request`에 필요한 요소는 내가 데이터를 가져오고자 하는 웹사이트의 URL 주소이다. 그래서 `url` 변수에 “http://codenamu.org/blog” 주소를 담았다. `request` 함수의 기본 사용 방법은 다음과 같다.

<code>
request(URL, function (err, response, html) {});
</code>

이렇게 가져온 소스코드를 `cheerio`를 이용해서 주로 `jQuery` 변수에 사용하는 `$`에 담는다.

## 블로그 제목 가져오기

<iframe src="http://jsfiddle.net/thechunsik/tdz8ukdg/5/embedded/" allowfullscreen="allowfullscreen" frameborder="0" height="410" width="100%"></iframe>

블로그 제목 정보가 담긴 데이터를 반복해서 가져와 별도로 만든 `post` 변수에 담았다.

이제 본격적으로 불러온 웹사이트에서 원하는 정보를 탐색해보자. 우선 원하는 정보가 담겨져 있는 HTML 구조를 파악해야 한다. 코드나무 블로그를 들어가서 HTML 구조를 살펴보자.

{% include image.html url="http://hoony.github.io/images/posts/inspector.png" description="사진 속 화면은 [파이어폭스 개발자 에디션](http://www.mozilla.org/firefox/developer/)(참조: [모질라가 만든 개발자를 위한 첫 브라우저: 파이어폭스 개발자 에디션](http://hacks.mozilla.or.kr/2014/11/mozilla-introduces-the-first-browser-built-for-developers-firefox-developer-edition/)) 브라우저의 ‘Inspector’ 기능(‘cmd + alt + c’)을 사용하여 HTML 구조를 살펴보는 모습이다." %}

현재 코드나무 블로그 웹사이트의 구조는 다음과 같다.

- 각 포스트는 `<div id="포스트번호" class="post ...."> </div>` 구조로 둘러쌓여 있다.
- 포스트 제목은 위 `<h2 class="entry-title"> <a> href="포스트 주소">제목</a></h2>`으로 담겨있다.
- 포스트 요약은 `<div class="entry-summary"><p>요약 내용</p></div>`으로 담겨 있다.
- 포스트 카테고리는 `<div class="entry-meta entry-footer"><span class="entry-categories"><a>카테고리1</a><a>카테고리2</a> </span> </div>`으로 담겨있다. 

자 이제 제목을 가져와보자. `cheerio`를 이용해서 웹사이트 HTML을 변수 `$`에 담았었다. 이제 원하는 제목 정보가 담긴 태그(`'.entry-title > a'`)를 변수 `$`를 이용해서 검색한다. 검색된 데이터를 변수 data에 담은 뒤 (`data = $(this);`) 제목(`data.text()`)과 포스트 주소(`data.attr('href')`)를 처리한다.

<code>
$('원하는 태그').each(function () {})
</code>

## 나머지 요약 정보와 카테고리 가져오기

<iframe src="http://jsfiddle.net/thechunsik/tdz8ukdg/4/embedded/" allowfullscreen="allowfullscreen" frameborder="0" height="600" width="100%"></iframe>
이어서 제목과 카테고리 정보를 가져왔다.

같은 방식으로 요약정보도 가져와보자. 요약 정보가 담긴 태그는 `.entry-summary > p`이다. 다음은 카테고리를 가져올 차례인데 카테고리는 이전 두 요소와는 다르게 한 포스트에 여러 개가 포함돼 있다. 이것을 해결해보자. 우선 모든 카테고리를 둘러싸고 있는 `.entry-categories` 태그를 가진 `span` 데이터를 불러온다. 그 다음 똑같은 방식으로 span 내에 포함된 모든 카테고리 요소: 카테고리1, 카테고리2를 반복문을 활용해서 다음과 같이 불러온다.
