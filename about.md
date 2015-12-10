---
layout: page
permalink: /about/index.html
title: Hoony, Jang
tags: [hoony, jang, civic hacker, thechunsik]
imagefeature: "hoony.jpg"
chart: true
---
<figure>
  <img src="{{ site.url }}/images/hoony.jpg" alt="Hoony, Jang">
  <figcaption>Hoony, Jang</figcaption>
</figure>

{% assign total_words = 0 %}
{% assign total_readtime = 0 %}
{% assign featuredcount = 0 %}
{% assign statuscount = 0 %}

{% for post in site.posts %}
  {% assign post_words = post.content | strip_html | number_of_words %}
  {% assign readtime = post_words | append: '.0' | divided_by:200 %}
  {% assign total_words = total_words | plus: post_words %}
  {% assign total_readtime = total_readtime | plus: readtime %}
  {% if post.featured %}
  {% assign featuredcount = featuredcount | plus: 1 %}
  {% endif %}
{% endfor %}


## Skills
- **Full Stack Programming**
- **Languages**: Node.js, Python

## Projects

#### **[wheredoesmymoneygo.kr](http://wheredoesmymoneygo.kr)** - Data Wrangling, Front-End Programming
- forked from [wheredoesmymoneygo.org](http://wheredoesmymoneygo.org/)
- developed with a designer, alice([Three Cicles](http://twitter.com/yeyeon91))
- visualization for how our governments are spending our money(tax)
- [source code](https://github.com/codeforseoul/wheredoesmymoneygo.kr)

#### **[getoutofdebt.kr](http://getoutofdebt.kr)** - Data Scraping, Wrangling, Front-End Programming(using MongoDB)
- developed at a [hackathon for transparency](http://transparency.codenamu.org/) hosted by [Code for Seoul](http://codeforseoul.org/)
- developed with a designer at [Slowalk]()
- visualization for how our governments are in depts
- source code
  - [homepage](https://github.com/codeforseoul/getoutofdebt.kr)
  - [scraping code](https://github.com/codeforseoul/getoutofdebt.kr-scraper)

#### **ethics.newstapa.org(not released)** - Front-End Programming, Visualization, with Newstapa
- developed to disclose public officials’ assets with Newstapa

#### **[noondo.kr](https://noondo.kr)** - Full-Stack Enginneering
- Angular.js, Semantic-UI, Parse
- crowd funding platform to create a customized bus route
- [source code](https://github.com/open-transit/noondo.kr)

#### **[Congress Report](https://github.com/codeforseoul/congress-report-web)** - Project Leading, Full-Stack Programming
- Python
- mailing service to help citizen monitor their congress man
- source code
  - [Web Page](https://github.com/codeforseoul/congress-report-web)
  - [Crawler](https://github.com/codeforseoul/congress-report)
  - [Mailer](https://github.com/codeforseoul/congress-report-mailer) 

## Experience

#### SK Communications, Seoul - Marketing Intern
- *Jan,  2012 - Feb,  2012*
- ‘Dream Project’ to make people’s dreams true
- business model in Nate/Cyworld

#### Second Commercial, Seoul - Intern
- *Sep, 2012 - Mar,  2013*
- mobile AD platform with a gamification system in mobile games

#### Creative Commons Korea, Seoul - Community Organizer, Web Programmer
- *Mar, 2014 - Feb, 2015*
- community organizing(creative commons korea community)
- global conference organizing(2014 creative commons korea global conference)
- web programming
- open (government) data consulting

#### Open Transit, Seoul - Co-Founder, Full-Stack Programmer
- *May, 2015 - Oct, 2015*
- developed a service named, ‘눈뜨면도착'
- crowd funding platform to create a customized bus route for people using public transportation regularly such as students or company employees

#### Mozilla Korea Community, Seoul - Mozillian(Volunteer)
- *May,  2013 - PRESENT*
- translation works(Mozilla Hacks Blog)

#### Code for Seoul, Seoul - Organizer, Full-Stack Programmer
- *May,  2014 - PRESENT*
- community organizing
- project managing, full-stack programming

#### Creative Commons Korea, Seoul - Volunteer
- *Dec,  2011 - PRESENT*



## Speaks
- **[Open Government Data Updates from around the World](https://pad.okfn.org/p/Open_Government_Data_updates_from_around_the_world)** - [Open Knowledge Festival 2014 ](http://2014.okfestival.org/)
- **[‘오픈데이터를 넘어(Beyond Opendata)’](http://sehub.blog.me/220055137876)** - Digital Society Innovation
- **[Hacking the Cities with Technology](http://2014con.cckorea.org/program/3/hacking-the-city-with-technology/)** - [Creative Commons Korea Global Conference](http://2014con.cckorea.org/)

## Articles

- **[[씨유피플] 정지훈 “혁신이 기득권 허문다”](http://www.bloter.net/archives/112928)** - [Bloter.net](http://www.bloter.net/)
- **[세금 감시, 시민 힘으로 ‘코딩’해요]()** - [Bloter.net](http://www.bloter.net/)
- **[GPL·AGPL·MPL…한눈에 보는 오픈소스SW 라이선스]()** - [Bloter.net](http://www.bloter.net/)

<!--
I am an PhD candidate in *ESE* at the [SEAS](http://www.seas.upenn.edu/) at **UPENN**. I am licensed as a Professional Engineer (P.E) to practice in the states of Texas, Massachusetts and California. I double majored in EECS and Mathematics during my undergraduate life at [MIT](http://www.mit.edu/), and currently focusing on Electrical Engineering for my post-graduate studies.

*[ESE]: Electrical and Systems Engineering
*[SEAS]: School of Engineering and Applied Science
*[MIT]: Massachusetts Institute of Technology
*[EECS]: Electrical and Computer Engineering
*[UPENN]: University of Pennsylvania


<figure>
	<img src="{{ site.url }}/images/Hossain-Mohd-Faysal.jpg" alt="Hossain Mohammad Faysal">
	<figcaption>At Bates Linear Accelerator Center</figcaption>
</figure>


I was born and brought up in Doha. Yes, its a desert peninsula, yes we have camels and falcons and all the other Middle Eastern traits/stereotypes you can think of.

<figure class="third">
	<a href="{{ site.url }}/images/about/1.jpg"><img src="{{ site.url }}/images/about/1-001.jpg"></a>
	<a href="{{ site.url }}/images/about/2.jpg"><img src="{{ site.url }}/images/about/2-001.jpg"></a>
	<a href="{{ site.url }}/images/about/3.jpg"><img src="{{ site.url }}/images/about/3-001.jpg"></a>
</figure>
<figure class="half">
	<a href="{{ site.url }}/images/about/4.jpg"><img src="{{ site.url }}/images/about/4-001.jpg"></a>
	<a href="{{ site.url }}/images/about/5.jpg"><img src="{{ site.url }}/images/about/5-001.jpg"></a>
</figure>
<figure class="third">
	<a href="{{ site.url }}/images/about/6.jpg"><img src="{{ site.url }}/images/about/6-001.jpg"></a>
	<a href="{{ site.url }}/images/about/7.jpg"><img src="{{ site.url }}/images/about/7-001.jpg"></a>
	<a href="{{ site.url }}/images/about/8.jpg"><img src="{{ site.url }}/images/about/8-001.jpg"></a>
	<figcaption>Doha at its full glory.</figcaption>
</figure>

At some point in the not-terribly-distant future, I hope to found a self-sustaining collective of clever people, for fun, profit(?), and the promotion of human life in the universe. This might wind up in Qatar, Bangladesh, Scandinavia, the Massachusetts Bay Area, the SF Bay Area, Japan, Germany, or the dustbin of overly idealistic plans. (Yes, I have a special bin for overly idealistic plans. In my district they can't be recycled with residential mixed paper.) The most challenging aspect of this concept is to curtail unproductive competition with other people who will inevitably have the same idea. (Some sort of cooperative federation...) I'm presently looking for people who might be interested in being a part of such an organization.

Anyways, for now I'm just working toward changing the face of Electrical Engineering forever. Not that I necessarily expect to succeed, but it's something to strive for, and it's a fun problem to work on.


Entrepreneur
Designer
***Engineer***
Inventor

I
make
stuff.


*Beautiful, practical, meaningful stuff.*


I make what I love.

*I love what I do.*


But over the years, I noticed that somehow, along the way, software designed to help us be creative, actually made us less creative. That's because we believe our best ideas emerge when we use pencils and paper.
So I set out to build tools that work the way I do.


Tools for the creative space — the 53 centimeters that magically link head, heart, and hand. Tools as simple as pencil and paper. Tools so essential, I  really can't imagine work without them.


For
the makers,
the creators,
the discoverers,
the original thinkers,
***This is the space to create.***
-->
