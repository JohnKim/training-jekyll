# Jekyll 이란 무엇인가요?

### 

> ### **기술 블로그 만의 Geek스러움이 부족했습니다. 그래서… 바꿨습니다!**
>
> &lt;kakao 기술 블로그가 GitHub Pages \(그리고 Jekyll\) 로 간 까닭은&gt;  
> [http://tech.kakao.com/2016/07/07/tech-blog-story/](https://www.gitbook.com/book/john-kim/training-jekyll/edit#)

Jekyll은 static site generator 중 하나입니다.  
템플릿 파일과 Markdown 기반의 문서 파일을 읽어들여 랜더링 과정을 통해 웹페이지로 변환시켜줍니다.

\(그림\) …

&gt;

…

Liquid \([https://shopify.github.io/liquid](https://shopify.github.io/liquid/)\) 는 Ruby 로 만들어진 가장 많이 사용되고 있는 템플릿 언어와 엔진으로 가장 많이 사용되고 있으며, Jekyll 에서 랜더링하는데 사용되고 있습니다.

[https://subicura.com/assets/article\_images/2016-06-20-server-side-rendering-with-react/template-engine.png](https://subicura.com/assets/article_images/2016-06-20-server-side-rendering-with-react/template-engine.png)

변환된 static files \(HTML, CSS, JS\) 를 Nginx\([https://nginx.or](https://nginx.org)g\)나 Apache\([https://httpd.apache.org](https://httpd.apache.org/)\)와 같은 웹서버를 통해 서비스하게 됩니다.

\(그림\)

Github 의 Github Pages 는 Jekyll 를 사용하는 프로젝트 리파지토리를 웹사이트로 동작하도록 하는 서비스를 제공하고 있으며, 이를 Github Pages 라고 합니다. Github Pages 를 사용하게 되면, 직접 웹서버를 설치하지 않고 Jekyll 기반의 프로젝트 저장소를 생성하는것 만으로도 웹서비스가 가능합니다.

\(그림\)



&gt;

Github Pages 를 통해 Jekyll 프로젝트를 웹서비스로 운영할 수 있지만, Jekyll 에 기능을 추가할 수 있는 Plugin 의 대부분은 사용할 수 없는 단점이 있습니다.

CMS로 유명한 Wordpress\(

[https://wordpress.org](https://wordpress.org/)

\)나 Ghost\(

[https://ghost.org/](https://ghost.org/)

\) 와 Jekyll 의 차이 점은 아래와 같습니다.

\(그림\) Static Site Generator

&gt;

Dynamic CMS

&gt;

static site generator 중에 Jekyll 이외에도, 아래와 같은 도구도 많이 사용됩니다.

* photo gallery websites 

[https://github.com/Jack000/Expose](https://github.com/Jack000/Expose)

* documentation website 

[https://www.gitbook.com/](https://www.gitbook.com/)

Jekyll 의 특징

Less Complexity

웹서버와 DB를 사용해야만 하는 일반적인 시스템과 달리, Static 한 파일을 서비스 할 수 있는 웹서버만 있으면 웹서비스를 할 수 있습니다. 또한 CDN \(Content Delivery Network\) 을 사용하거나 AWS 의 S3 스토리지만 있어도 가능합니다.

Speed

Static 한 파일만을 서비스 한다는 것은, 속도의 장점도 클 수밖에 없습니다. 일반적인 시스템의 웹서버에서 DB 에 데이터를 조회해서 화면에 보여주어야 하는 것은 상대적으로 상당한 시간과 자원을 소비하게 됩니다.

Scalability

부하 증가에 따른 Scale Out\(서버 수량을 늘려서 Capacity 를 확보 함\) 할 경우 일반적인 시스템의 경우 웹서버와 DB 의 서로 다른 방식의 확장을 고려해야 하고, 특별히 DB 의 경우 Scale Out 에 많은 고민이 필요합니다. Static 한 서비스의 경우, DB가 없으므로 웹서버만 확장하면 되므로 상대적으로 고민할 부분이 크지 않습니다.

그외에도, 전체적인 아키텍처가 간단하여 관리가 쉽고, 보안을 위해 고려해야할 부분도 적습니다.

장점만 있는 것은 아닙니다. 작성되는 글을 실시간으로 서비스에 반영할 수 있는 일반적은 CMS 와 달리, 새로은 글을 작성하거나 수정할 경우 다시 변환해주어야만 합니다. 다만, 많은 글쓴이가 수시로 작성해야 하는 웹서비스가 아니라면, 큰 문제가 되지 않을 수 있습니다.

