# Jekyll에 대한 설명

> ### **기술 블로그 만의 Geek스러움이 부족했습니다. 그래서… 바꿨습니다!**
>
> &lt;kakao 기술 블로그가 GitHub Pages \(그리고 Jekyll\) 로 간 까닭은&gt;  
> [http://tech.kakao.com/2016/07/07/tech-blog-story/](https://www.gitbook.com/book/john-kim/training-jekyll/edit#)

Jekyll은 static site generator 중 하나이며 Ruby 로 개발되어 있습니다.  
템플릿 파일과 Markdown 기반의 문서 파일을 읽어들여 랜더링 과정을 통해 웹페이지로 변환시켜줍니다. 

Liquid \([https://shopify.github.io/liquid](https://shopify.github.io/liquid/)\) 는 Ruby 로 만들어진 가장 많이 사용되고 있는 템플릿 엔진으로 가장 많이 사용되고 있으며, Jekyll 에서 랜더링하는데 사용되고 있습니다.

![](/images/template-engine.png)

변환된 static files \(HTML, CSS, JS\) 를 Nginx\([https://nginx.or](https://nginx.org)g\)나 Apache\([https://httpd.apache.org](https://httpd.apache.org/)\)와 같은 웹서버를 통해 서비스할 수 있습니다.

Github 의 Github Pages 서비스는 Jekyll 를 사용하는 프로젝트 리파지토리를 웹사이트로 동작하도록 하는 기능을 제공하고 있습니다. Github Pages 를 사용하게 되면, 직접 웹서버를 설치하지 않고 Jekyll 기반의 프로젝트 저장소를 생성하는것 만으로도 웹서비스가 가능합니다.

Github Pages 를 통해 Jekyll 프로젝트를 웹서비스로 운영할 수 있어 상당히 유용하지만, Jekyll 에 기능을 추가할 수 있는 Plugin 중 일부는 동작하지 않는 단점이 있습니다.

CMS\(Content Management System\)로 유명한 Wordpress\([https://wordpress.org](https://wordpress.org/)\)나 Ghost\([https://ghost.org/](https://ghost.org/)\) 는 웹서버,  CMS서버 그리고 DBMS으로 구성되며 Jekyll 과는 분명한 차이점이 있습니다.

**Jekyll** : Nginx 에 Jekyll 에서 변환된 HTML/CSS/JS 를 올려 서비스 할 수 있습니다.  
**Wordpress** : Nginx - Wordpress - MySQL 구조로, Nginx 와 DB 사이의 서버에 static 파일들과 동적 로직이 포함되어 있고, DB 구성도 필요합니다.

static site generator 중에 Jekyll 이외에도, 아래와 같은 도구도 많이 사용됩니다.

* photo gallery websites - [https://github.com/Jack000/Expose](https://github.com/Jack000/Expose)

* documentation website - [https://www.gitbook.com/](https://www.gitbook.com/)

### Jekyll 의 특징

**Less Complexity**

웹서버와 DB를 사용해야만 하는 일반적인 시스템과 달리, Static 한 파일을 서비스 할 수 있는 웹서버만 있으면 웹서비스를 할 수 있습니다. 또한 CDN \(Content Delivery Network\) 을 사용하거나 AWS 의 S3 스토리지만 있어도 가능합니다.

**Speed**

Static 한 파일만을 서비스 한다는 것은, 속도의 장점도 클 수밖에 없습니다. 일반적인 시스템에서는 DB 에 데이터를 조회해서 화면에 보여주어야 하기 때문에 상대적으로 많은 시간과 컴퓨팅 자원을 소비하게 됩니다.

**Scalability**

부하 증가에 따른 Scale Out\(서버 수량을 늘려서 Capacity 를 확대함\) 할 경우 일반적인 시스템의 경우 웹서버와 DB 의 서로 다른 방식의 확장을 고려해야 하고, 특별히 DB 의 경우 Scale Out 에 많은 고민이 필요합니다. Static 한 서비스의 경우, DB가 없으므로 웹서버만 확장하면 되므로 상대적으로 고민할 부분이 크지 않습니다.

그외에도, 전체적인 아키텍처가 간단하여 관리가 쉽고, 보안을 위해 고려해야 할 부분도 상대적으로 많지 않습니다.

물론 장점만 있는 것은 아닙니다. 작성되는 글을 실시간으로 서비스에 반영할 수 있는 일반적은 CMS 와 달리, 새로운 글을 작성하거나 수정할 경우 다시 변환해주어야만 합니다. 다만, 많은 글쓴이가 수시로 작성해야 하는 웹서비스가 아니라면, Static Site Generator 도 큰 문제가 되지 않을 것입니다.

> Scale Up 과 Scale Out
>
> Scale Up 은 시스템의 처리량을 늘리기 위하여 메모리, CPU 또는 디스크 용량을 늘리는 방법을 말하며, Scale Out 은 서버 대수를 늘려더 많은 처리를 할 수 있도록 하는 것입니다. 물리적인 하드웨어의 가격 하락과 무중단 서버 확장의 이점이 있는 Scale Out 을 더 선호하고 있습니다만, 상황에 따라 어떤 방식으로 처리량을 늘릴지는 잘 판단해야 합니다.



