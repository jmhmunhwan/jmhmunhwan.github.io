---
layout: post
title: 깃허브 페이지 작성해보기
subtitle: 5분만에 따라해보기
gh-repo: jmhmunhwan/jmhmunhwan.github.io
gh-badge: [star, fork, follow]
category : devlog
tags: blog
comments: true
---

블로그 작성을 해보기로 결심한 후에 저번에 작성한 [어떤 블로그를 쓸 것인가?](https://jmhmunhwan.github.io/devlog/2019/01/21/How-I-Can-Choose-Appropriate-Blog/)
포스트처럼 여러 블로그 플랫폼을 알아보고 최종적으로 깃허브 페이지를 이용하기로 결정했다. 

![Blog](http://www.ybrikman.com/assets/img/blog/github-pages/github-pages.png)

깃허브 페이지를 무작정 만들어보려고 하니, 할 게 너무 많아서 잘 되어 있는 걸 가져와야겠다고 생각이 들었다. [깃허브에서 Jekyll 검색](https://github.com/search?q=jekyll)
하면 여러 테마들을 볼 수 있다. 그런데 내가 필요한 것들이 다 구성되어 있는 걸 찾기가 힘들었다.(깃허브 페이지는 필요한 기능들을 하나씩 다 구성해줘야한다.)

### 필요한 기능

```
  1. 카테고리 구성
  2. 댓글
  3. 통계
```

구글링하다보니 [박민(isme2n)님 깃허브 페이지](https://isme2n.github.io/) 가 제일 맘에 들어서 가져다 쓰기로 정했다.

### 맘에 드는 테마 가져오기

---

  1. 라이센스 확인
  2. fork
  3. config 등 수정

---
우선 맘에 드는 테마를 가져오려고 해도, 이게 지적 재산권, 저작권 침해인지 확인을 해야한다.
[박민(isme2n)님 깃허브 페이지 라이센스](https://github.com/isme2n/isme2n.github.io/blob/master/LICENSE.md)
확인해보니 `MIT License`라 편히 사용해도 되는 것 같다. 그래도 많은 사람들이 댓글로 써도 되는지 물어보고 사용하는 걸로 보인다.

>(  1. ~~라이센스 확인~~ )

fork 하는 법은 [박민(isme2n)님 깃허브 페이지](https://isme2n.github.io/) 여기서 fork 버튼만 누르면 된다.

그리고 깃허브 페이지는 ``본인계정``.github.io 로만 만들어지므로 ``Settings``에서 Repository 를 Rename 해주면 된다.
<br>(ex. https://jmhmunhwan.github.io/)

>(  2. ~~fork~~ )

fork 받은 것들을 살펴보면 수정해야 할 것들이 많다. 우선 [_config.yml 파일](https://github.com/jmhmunhwan/jmhmunhwan.github.io/blob/master/_config.yml)
에 공용적으로 쓰이는 환경 설정 정보들이 많으므로 이걸 수정했다. 살펴보니 **댓글**은 [DISQUS](https://disqus.com/)로, 
**통계**는 [Google Analytics](https://analytics.google.com/) 로 사용하고 있다.
나도 해당 기능을 쓰고 싶으니 id 같은 값만 내걸로 바꿔서 쓰면 될 듯 하다. 

```html
# Set your Google Analytics id to receive `pageview` events.
# To remove Google Anaylics from your page, remove the line below.
google_analytics:

# Setting a disqus shortname will enable the comment section on pages with `comments: true` in the front matter
disqus_shortname:
```

그리고 [_includes/contents.html](https://github.com/jmhmunhwan/jmhmunhwan.github.io/blob/master/_includes/contents.html) 에서는
**구글 애드센스**가 적용되어 있다. 아래와 같이 ``data-ad-client``를 내걸로 바꿔주면 끝.

```html
<div class="markdown-body">
  <script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
                <!-- 블로그-하단-반응형 -->
                <ins class="adsbygoogle"
                    style="display:block; width:98%; height:300px;"
                    data-ad-client="             "
                    data-ad-slot="2380354290"
                    data-ad-format="auto"></ins>
                <script>
                (adsbygoogle = window.adsbygoogle || []).push({});
                </script>
                <br/>
  {{ post.content }}
</div>
<br/>
<br/>
<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- 블로그-하단-반응형 -->
<ins class="adsbygoogle"
    style="display:block; width:98%; height:300px;"
    data-ad-client="             "
    data-ad-slot="2380354290"
    data-ad-format="auto"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>
```

>(  3. ~~config 등 수정~~ )

결과 화면도 보여주고 싶지만 문제가 있어  https://jmhmunhwan.github.io/ 링크로 대체..

위 방법으로 하면 원작자님이 쓰던 것들도 다 들고와서 좀 난감하다. About.html 같은 건 수정하면 되지만, 포스트들은 하나씩 삭제해야한다.
이건 **Git**으로 commit, push 해야겠다.


### 포스팅하기

`_posts` 폴더에 md 파일을 작성하면 알아서 포스팅이 된다. 테마별로 각각 js를 이용해서 포스팅 되도록 코딩되어 있기 때문에 맞춰서 하면 된다.
2019-02-11-Github Page.md 처럼 YYYY-MM-DD-TITLE.md 로 저장하면 된다. 이 테마에서는 ``_featured_categories``, ``_featured_tags`` 로 카테고리를 구별하게 만들어져있다. 대분류가 카테고리, 소분류가 태그로 이해하면 된다. 실제 적용은 아래처럼 하면 된다.

```
---
layout: post
title: 깃허브 페이지 작성해보기
subtitle: 5분만에 따라해보기
gh-repo: jmhmunhwan/jmhmunhwan.github.io
gh-badge: [star, fork, follow]
category : devlog
tags: blog
comments: true
---
```

tag 에 적어놓은 ``blog`` 처럼 기존에 없는 걸 추가할 경우에는 해당 폴더에 다른 md 파일들을 보고 양식을 맞추어 새롭게 하나 만들어주면 된다.
(ex. [devlog-blog.md 파일](https://github.com/jmhmunhwan/jmhmunhwan.github.io/edit/master/_featured_tags/devlog-blog.md) )

```
---
layout: tag-blog
title: Blog
slug: blog
category: devlog
menu: false
order: 3
---
```

마크다운 사용법에 대해서는 따로 기술하겠다.
이만 뿅.
