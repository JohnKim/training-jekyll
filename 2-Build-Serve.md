# Jekyll 빌드 및 실행

jekyll 에서는 빠르게 시작할 수 있는 도구를 제공합니다. 이 도구를 사용하게 되면, 기본적으로 제공되는 UI 테마를 사용하여 웹사이트를 만들 수 있습니다. 실무에서는 직접 개발한 UI 를 사용하는 경우가 많기 때문에 이런 방식이 사용되는 경우는 거의 없습니다. 다만, 동작의 원리를 이해하기 위한 용도 또는 간단한 웹페이지 생성을 위하여 이런 과정이 사용될 것입니다.

```bash
$ jekyll new website
$ cd website
$ jekyll serve
```

`http://localhost:4000` 으로 접속하면 생성된 웹화면을 볼 수 있습니다.

`jekyll new` 로 프로젝트를 생성하면, Default 로 `minima` 라는 UI 테마를 적용하여 웹사이트가 빌드되어 생성되도록 설정되게 됩니다.

```
├── Gemfile
├── _config.yml
├── _posts
│   └── 2017-03-17-welcome-to-jekyll.markdown
├── about.md
└── index.md
```

`_config.yml` 은 Jekyll 에서 개발하는 페이지에서 사용할 수 있는 변수들을 설정하거나, 빌드시 필요한 정보를 설정하게 됩니다.

```
# _config.yml

title: Your awesome title
email: your-email@domain.com
description: > # this means to ignore newlines until "baseurl:"
  Write an awesome description for your new site here. You can edit this
  line in _config.yml. It will appear in your document head meta (for
  Google search results) and in your feed.xml site description.
baseurl: "" # the subpath of your site, e.g. /blog
url: "" # the base hostname & protocol for your site, e.g. http://example.com
twitter_username: jekyllrb
github_username:  jekyll

# Build settings
markdown: kramdown
theme: minima
gems:
  - jekyll-feed
exclude:
  - Gemfile
  - Gemfile.lock
```

`jekyll serve` 는 빌드과정을 거쳐 내장된 서버를 실행하여 개발자가 웹브라우져에 접속하여 확인할 수 있도록 합니다.

`jekyll server` 를 실행하면, 아래와 같이 `_site` 폴더가 생성되어 그 안에 빌드된 파일들이 생성됩니다. 여기에 생성된 파일을 웹서버\(Nginx 또는 Apache 같은\)에 올려 서비스 할 수 있습니다.

```
├── Gemfile
├── _config.yml
├── _posts
│   └── 2017-03-14-welcome-to-jekyll.markdown
├── _site
│   ├── about
│   │   └── index.html
│   ├── assets
│   │   └── main.css
│   ├── feed.xml
│   ├── index.html
│   └── jekyll
│       └── update
│           └── 2017
│               └── 03
│                   └── 14
│                       └── welcome-to-jekyll.html
├── about.md
└── index.md
```

> **페이지 주소\(URL\)에 제목이 있는 이유는 무엇일까?**
>
> 검색엔진의 검색 결과를 상위에 노출하기 위한 것을 총칭하여 SEO\(Search-Engine Optimization\) 라고 부른다. HTML 테그중 meta 를 사용하여 웹페이지와 관련된 설명을 추가하거나, URL 에 검색어가 될 수 있는 단어를 노출하는 것으로 검색 결과 상위에 노출될 확률을 높히는 것이다. 근래 대부분의 블로그 서비스에서는 이와 같이 URL 에 제목을 노출하는 경우가 많다.



