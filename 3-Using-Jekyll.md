# Jekyll 사용하기

본 장에서는 `jekyll new` 를 사용하지 않고, 기본적으로 제공하는 UI 테마를 없이 직접 파일을 생성하여 처음부터 개발해보도록 합니다.

Jekyll 기반의 웹사이트를 개발한 프로젝트 폴더를 생성합니다.

```
$ mkdir website
$ cd website
```

### 1.Template

프로젝트 폴더에서, 아래와 같이 `index.html` 파일을 생성합니다.

```
---
hello_text: "Hello there!"
show_footer: false
fruit:
  - name: apple
    cost: $1
    color: red
  - name: banana
    cost: $2
    color: yellow
  - name: orange
    cost: $1.50
    color: orange
---
<!doctype html>
<html lang="en">
  <head>
    <title>Sample 1</title>
  </head>
  <body>
    <h1>Hello World</h1>
    <p>{{ page.hello_text }}</p>

    <ul>
      {% for item in page.fruit %}
        <li>{{ item.name }}, cost: {{ item.cost }}, color: {{ item.color }}</li>
      {% endfor %}
    </ul>

    {% if page.show_footer %}
      <footer>I am a footer</footer>
    {% endif %}
  </body>
</html>
```

`jekyll serve` 를 실행하면, 아래와 같이 `_site` 폴더가 생성되어 빌드된 index.html 파일이 생성되게 됩니다.

```
.
├── _site
│   └── index.html
└── index.html
```

이제 [http://localhost:4000](http://localhost:4000) 에 접속하면 `_site/index.html` 의 내용이 웹브라우저에 랜더링 될 것입니다.

`index.html` 의 최상단 앞뒤에 `---` 로 구분되어 있는 영역을 Front Matter, 즉 머릿말 이라고 합니다. 여기에 파일에서 사용할 변수와 데이터를 정의할 수 있습니다.

그리고 HTML 중간 중간에 Liquid 템플릿 문법을 사용하여 작성하고, Jekyll 이 이 파일을 빌드하여 HTML 로 변환하게 될 것입니다. index.html 은 HTML 과 함께 Liquid 템플릿 문법을 사용하여 작성하였으므로, 통상적으로 HTML 이라고 부르기보다는 템플릿 파일이라고 부릅니다.

Liquid 문법은 지정하는 변수를 보여주는`{{ 변수 }}` 와 로직을 넣을 수 있는 `{% 로직 문 %}` 이 있습니다.

### 2. Layouts

Layout 이란 개발해야 할 웹페이지마다 공통적으로 들어갈 **부모화면**이라고 할 수 있습니다. 주로, Header 와 Footer 영역이나, 모든페이지에 포함되어야 할 Javascript 또는 CSS 파일을 로드하는 부분이 여기에 개발됩니다.

Layout 을 미리 개발해 놓은 후 각 웹페이지 템플릿 파일을 개발하게 되면, 개발자는 모든 페이지에 공통 부분을 중복해서 개발하지 않아도 될 것입니다.

지금부터 개발하게 될 웹사이트는 전세계에서 가장 많이 사용되고 있는 웹 프레임워크인 Bootstrap 을 기반으로 개발하도록 합니다.

> Bootstrap \([http://getbootstrap.com\](http://getbootstrap.com%29\)  
> Bootstrap is **the most popular HTML, CSS, and JS framework** for developing responsive, mobile first projects on the web.

`_layouts/default.html` 파일을 아래와 같이 생성합니다.

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>{{ page.title }}</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">
  </head>

  <body>

    <nav class="navbar navbar-default navbar-fixed-top">
      <div class="container">
        <div class="navbar-header">
          <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#navbar" aria-expanded="false" aria-controls="navbar">
            <span class="sr-only">Toggle navigation</span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
          </button>
          <a class="navbar-brand" href="#">SAMPLE SITE</a>
        </div>
        <div id="navbar" class="collapse navbar-collapse">
          <ul class="nav navbar-nav">
            <li><a href="/">Home</a></li>
            <li><a href="/posts.html">Posts</a></li>
            <li><a href="/about.html">About</a></li>
          </ul>
        </div>
      </div>
    </nav>

    <br/>

    <div class="container">
      {{ content }}
    </div>

    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>

  </body>
</html>
```

이 layout 파일을 사용하는 템플릿 페이지의 내용은 Jekyll 을 통해 빌드될 때 `{{ content }}` 영역에 들어가 HTML 로 변환되게 될 것입니다.  
그리고 layout 파일에서는 layout을 사용하는 템플릿 페이지 파일안의 Front Matter 에 정의한 변수를 가져다 사용할 수도 있습니다. `{{ page.title }}` 은 layout 을 사용하는 템플릿 페이지에 정의한 title 변수입니다.

이제 이 layout 을 사용하는 템플릿 페이지 파일을 만들어 봅니다.

좀전에 만들었던 `index.html` 파일을 다시 작성합니다. Header 와 Footer 영역은 앞에 layout 에서 구현하였으므로, `index.html` 에서는 Header 와 Footer 에 대한 코드를 삭제합니다. 그리고 Front Matter 로 title 변수를 설정하여 layout 에서 사용할 수 있도록 합니다.

```
---
layout: default
title: Home
fruit:
  - name: apple
    cost: $1
    color: red
  - name: banana
    cost: $2
    color: yellow
  - name: orange
    cost: $1.50
    color: orange
---
<div class="page-header">
  <h1>Sticky footer with fixed navbar</h1>
</div>
<p>
  <ul>
    {% for item in page.fruit %}
    <li>{{ item.name }}, cost: {{ item.cost }}, color: {{ item.color }}</li>
    {% endfor %}
  </ul>
</p>
```

이제 다시 `jekyll serve` 를 실행하고, [http://localhost:4000](http://localhost:4000) 에 접속하면, `_layouts/default.html` 의 `{{ content }}` 영역에 `index.html` 의 내용이 삽입되고 변수를 사용한 결과를 확인할 수 있습니다.

`_site` 폴더 안의 파일 내용을 통해 확인해 보도록 합니다.

### 3. Includes

Layout 은 페이지의 틀이나 배경이라고 한다면, Include 는 공통으로 사용될만한 영역을 별도로 분리해 놓는 것입니다. 다른 템플릿 엔진에서는 partial 이라고 부르기도 합니다. 화면을 구성하는 조각을 별도로 분리해서 개발해 놓는 것입니다.

본 실습에서는 Youtube 동영상을 보여주는 부분을 Include 로 만들어 보도록 합니다.

`_includes/youtube.html` 파일을 아래와 같이 작성합니다.

```
<div class="spacing youtube">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/{{ include.youtube_id }}" frameborder="0" allowfullscreen></iframe>
</div>
```

이렇게 작성한 include 파일은 여러가지 템플릿 페이지에서 사용할 수 있습니다. 위의 예제와 같이 특정 변수를 넘길수도 있습니다. 위의 include 파일을 앞에 만든 `index.html` 에 원하는 위치에 아래 코드를 넣도록 합니다.

```
{% include youtube.html youtube_id="8A2t_tAjMz8" %}
```

이 코드는 include 하면서 `youtube_id` 라는 변수를 설정하는 예시이며, `include/youtube.html` 에서는 이 변수를 사용할 수 있습니다.

`_site` 폴더 안의 다시 빌드된 파일 내용을 통해 확인해 보도록 합니다.

### 4. Posts

마지막으로는 블로그와 같이 문서 \(또는 글\)를 작성하고 이를 목록으로 보여주는 부분을 실습하도록 하겠습니다.

먼저 `_posts/2017-03-17-welcome-to-jekyll.md` 파일을 아래와 같이 생성하고, Markdown 문법으로 글을 작성합니다.

```
---
layout: default
---

Lorem ipsum dolor sit amet, consectetur adipiscing elit.
Maecenas at tellus sed erat egestas dictum sed ac enim.
Fusce sollicitudin turpis nec urna egestas pellentesque.

Suspendisse ultricies ex vitae dui tempus dignissim.
Morbi sit amet dui molestie, aliquam urna id, rhoncus tellus.
Aliquam venenatis a velit in scelerisque.

Donec orci felis, feugiat eget ex sed, convallis sollicitudin dui.
Proin ut nisl vestibulum, vestibulum sapien non, lobortis velit.
Sed sodales, lorem et vulputate dignissim, felis dolor lobortis leo, id pretium magna libero non orci.

Morbi interdum augue tellus, vel gravida sapien euismod vitae.
```

파일명은 일반적으로 생성\(발행\) 일자와 제목으로 만들게 됩니다.

그리고, `_posts/2017-03-16-sample.md` 파일을 하나 더 만들어 글을 작성해 봅니다.

현재 두건의 글을 작성하였고 글 목록을 보여주는 페이지를 만들어 보도록 합니다.

`posts.html` 파일을 아래와 같이 작성합니다.

```
---
layout: default
title: Blog Page
---
<ul>
  {% for post in site.posts %}
    <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
```

Jekyll 은 \_posts 폴더의 모든 파일 목록을 site.posts 를 통해 배열로 받아 사용할 수 있습니다.

`_site` 폴더 안의 구조를 보면, 작성한 파일들이 일자별 폴더와 함께 생성된 것을 확인할 수 있습니다.

```
├── _site
│   ├── 2017
│   │   └── 03
│   │       ├── 16
│   │       │   └── sample.html
│   │       └── 17
│   │           └── welcome-to-jekyll.html
│   ├── index.html
│   └── posts.html
```

[http://localhost:4000](http://localhost:4000) 에 접속하면 지금까지 개발한 사이트를 확인할 수 있습니다.

> 샘플로 만든  'Lorem ipsum dolor sit amet...' 문장은 사실상 특별한 의미가 없는 문장으로, 다양한 문자가 섞여 있고 문자의 조합에서 글자의 간격이 잘 드러나기 때문에 샘플이나 테스트 용으로 많이 사용되고 있다.  
> 참조 : [http://www.lipsum.com](http://www.lipsum.com)



