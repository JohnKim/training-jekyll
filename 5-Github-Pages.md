# Github Pages

많은 개발자들은 Github 을 통해 포트폴리오나 개발 이력 또는 기술 블로그를 Github Pages 를 통해 공유 하고 있습니다.  
\(예, [https://biomadeira.github.io/sustain](https://biomadeira.github.io/sustain/) \)

이제, 앞서 구축한 Jekyll 프로젝트를 저번 주 실습 때 생성한 `training-github` 프로젝트 저장소에 올려보도록 할 것입니다.  
`training-github` 프로젝트 저장소에 `gh-pages` 브랜치를 생성하고 여기에 Jekyll 프로젝트를 저장하면, `http://[본인계정].github.io/training-github` 으로 접속할 수 있습니다.

Github 은 프로젝트 저장소의 `gh-pages` 브랜치에 있는 파일을 URL 로 접속할 수 있도록 하고 있으며, Jekyll을 기본적으로 지원하고 있습니다.

우선, 원격 리파지토리에 있는 프로젝트를 `git clone` 명령으로 PC 에 가져 옵니다. 이미 `git clone` 한 프로젝트가 있다면 이 단계는 그냥 넘어 갑니다.

```
$ git clone https://github.com/[본인이생성한계정]/training-github.git
$ cd training-github
```

gh-pages 브랜치를 생성하고 이 브랜치로 이동합니다.

```
$ git branch gh-pages
$ git checkout gh-pages
```

> 브랜치 리스트 확인하기 : `git branch`  
> 현재 브랜치 확인하기 : `git status`

이제 gh-pages 브랜치에서 .git 폴더를 제외한 모든 파일을 삭제 합니다.  
.git 폴더는 git 저장소에 대한 정보를 담고 있으며, 만약 이 폴더가 없다면, 더이상 git 저장소와는 상관 없는 상태가 될 것입니다.

그리고, 이전에 개발했던 Jekyll 프로젝트의 모든 파일을 옮겨 저장합니다.

원격 저장소에 이 모든 파일을 업로드 하기 전에 git 에 관리되지 않아야 하는 파일 또는 폴더를 설정해주는 `.gitignore` 파일을 생성합니다.  
.`.gitignore` 파일 내용은 아래와 같습니다.

```
_site
```

\_site 폴더는 git 에 저장되어 관리될 필요가 없습니다. 개발자가 Jekyll 프로젝트를 git clone 으로 받아 직접 jekyll 명령어로 생성하면 되기 때문입니다. 이것은 JAVA 개발시 Maven 이나 Gradle 로 필요한 라이브러리를 다운받기 때문에 git 에 관리할 필요 없는 것과 마찬가지 입니다.

> `.gitignore`** 파일을 보다 쉽게 만드는 방법은?**
>
> 보통 프로젝트 리파지토리를 만들고 가장 먼저 하는 작업은 `.gitignore` 입니다. OS나 IDE 또는 에디터에 따라 다르고, 사용하는 개발언어에 따라서도 다릅니다.   
> 좀더 쉽게 `.gitignore` 파일을 작성하기 위하여, 자동으로 생성하는 https://www.gitignore.io/ 사이트를 이용할 수 있습니다.



이제 원격 저장소에 `git push` 명령을 통해 업로드 합니다.

```
$ git push origin gh-pages
```

Github 에서 실제로 정상적으로 업로드 되었는지 보고, `http://[본인계정].github.io/training-github`를 통해 웹페이지에서 보이는지 확인합니다.

그 외에도, `[본인계정].github.io`라는 이름으로 프로젝트 리파지토리를 생성하고 여기에 Jekyll 프로젝트를 저장하게 되면, 바로 `http://[본인계정].github.io/`에서 확인할 수 있습니다. \(반드시 master 에 생성해야 함\)

![](/images/Jekyll-GitHubPages.png)

