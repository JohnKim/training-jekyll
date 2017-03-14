본 장에서는 `jekyll new` 를 사용하지 않고, 기본적으로 제공하는 UI 테마를 없이 직접 파일을 생성하여 처음부터 개발해보도록 합니다.

내용과 예제는 http://jekyll.tips 에 있는 내용 중 기본적인 부분을 참조하여 작성되었습니다. 

Jekyll 기반의 웹사이트를 개발한 프로젝트 폴더를 생성합니다.

```
$ mkdir website
$ cd website
```

프로젝트 폴더에서, 아래와 같이 index.html 파일을 생성합니다.

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

jekyll serve 를 실행하면, 아래와 같이 \_site 폴더가 생성되어 빌드된 index.html 파일이 생성되게 됩니다.

```
.
├── _site
│   └── index.html
└── index.html
```

이제 http://localhost:4000 에 접속하면 \_site/index.html 를 볼 수 있습니다.

index.html 의 최상단 앞뒤에 --- 로 구분되어 있는 영역을 Front Matter, 즉 머릿말 이라고 합니다. 여기에 파일에서 사용할 변수와 데이터를 정의할 수 있습니다. 

그리고 HTML 중에 Liquid 템플릿 문법을 사용하였으며, Jekyll 이 이 파일을 빌드하여 HTML 로 변환하게 될 것입니다. index.html 은 HTML 과 함께 Liquid 템플릿 문법을 사용하여 작성하였으므로, 통상적으로 HTML 이라고 부르기보다는 템플릿 파일이라고 부릅니다. 


