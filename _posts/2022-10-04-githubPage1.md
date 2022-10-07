---
layout: single
title: "깃허브 페이지 만들기(1)"
classes: wide
toc : true
toc_sticky: true
categories:
  - 깃허브 페이지 만들기
tags:
  - minimal Mistakes
  - github pages
---  


# Github pages 블로그 만들기
지킬(Jekyll)은 정적 사이트 생성기로 일반 텍스트를 정적 웹사이트 및 블로그로 변환합니다. Github Pages는 Jekyll을 기반으로 무료로 Gihub를 사용하여 사이트를 배포할 수 있습니다.  
[공식 홈페이지](https://jekyllrb.com/){:target="_blank"}     

***

# 지킬(Jekyll) 테마
Jekyll 테마는 다른 사용자들이 이미 구성해서 배포한 template이며, 많은 무료 template이 공개되어 있습니다. 무료 테마들 중에서 인기있는 Minimal Mistakes 테마를 적용해서 블로그를 만들어 봅시다.  

[Github minimal Mistakes 템플릿](https://github.com/mmistakes/minimal-mistakes){:target="_blank"}    

***

# 사전 작업
Github 계정이 있어야 합니다. Github에 대한 내용은 다시 준비하겠습니다. 우선은 구글 검색 등을 통해서 가입하고 진행하면 됩니다.  

***

# 1. minimal-mistakes 테마 적용하기
깃허브 레포(https://github.com/mmistakes/minimal-mistakes) 에 접속하여 우측 상단의 fork 버튼을 클릭합니다.  
fork한 repository 명칭을 **(본인의 github 계정이름).github.io** 로 변경합니다.  
예) kig2929kig.github.io     

![image](https://user-images.githubusercontent.com/47412229/193731543-b354b308-fe0a-45e3-b522-051951516984.png)

***

# 2. _config.yml 편집

## 2-1. 테마 스킨
```
minimal_mistakes_skin    : "air" # "air", "aqua", "contrast", "dark", "dirt", "neon", "mint", "plum", "sunrise"
```   
[테마 스킨 목록](https://mmistakes.github.io/minimal-mistakes/docs/configuration/#skin){:target="_blank"}    

![image](https://user-images.githubusercontent.com/47412229/193731715-a2c42622-5826-49cf-a21a-be02d9f41a6e.png)

## 2-2. 사이트 설정

```
# Site Settings
locale                   : "ko-KR"
title                    : "사이트 제목 표시줄"
title_separator          : "-"
subtitle                 : # site tagline that appears below site title in masthead
name                     : 이름 # "Your Name"
description              : 어마 무시한 웹 사이트 # "An amazing website."
url                      : "https://kig29kig.github.io" # the base hostname & protocol for your site e.g. "https://mmistakes.github.io"
baseurl                  : # the subpath of your site, e.g. "/blog"
repository               : "kig29kig/kig29kig.github.io" # GitHub username/repo-name e.g. "mmistakes/minimal-mistakes"
teaser                   : # path of fallback teaser image, e.g. "/assets/images/500x300.png"
logo                     : # path of logo image to display in the masthead, e.g. "/assets/images/88x88.png"
masthead_title           : # overrides the website title displayed in the masthead, use " " for no title
```   

![image](https://user-images.githubusercontent.com/47412229/193730602-e3dd7235-a825-481a-bb1a-3d6570bec9a0.png)  

~~name~~, description은 웹 사이트에 대한 정보를 입력하는 곳으로 실제 보여지는 웹사이트에서는 나타나지 않습니다.  

## 2-3. 사이트 작성자  

```
# Site Author
author:
  name             : "INGOO KANG" # "Your Name"
  avatar           : # path of avatar image, e.g. "/assets/images/bio-photo.jpg"
  bio              : "어마 무시한 웹 사이트" # "I am an **amazing** person."
  location         : "Republic of Korea" # "Somewhere"
  email            :
  links:
    - label: "Email"
      icon: "fas fa-fw fa-envelope-square"
      url: "mailto:kig2929kig@naver.com"
    - label: "Website"
      icon: "fas fa-fw fa-link"
      # url: "https://github.com/kig2929kig"
    - label: "Twitter"
      icon: "fab fa-fw fa-twitter-square"
      # url: "https://twitter.com/"
    - label: "Facebook"
      icon: "fab fa-fw fa-facebook-square"
      # url: "https://facebook.com/"
    - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/kig2929kig"
    - label: "Instagram"
      icon: "fab fa-fw fa-instagram"
      # url: "https://instagram.com/"
```  

![image](https://user-images.githubusercontent.com/47412229/193735761-dce26b49-4a9a-451d-aad6-902ad7a6ed01.png)  

```
avatar : "/assets/images/그림파일.jpg"
```
`/assets/` 폴더에 images 폴더를 만들고 그림파일을 저장 후 적용하면 저장된 그림파일이 보여집니다. 보통은 개인 사진을 저장합니다.
  
  
## 2-4. POST 게시물 만들기

`/_posts/` 폴더를 만들고 폴더 안에 포스팅할 파일을 작성하면 됩니다. 예) 2022-10-04-firtst_posting.md  
확장자는 .md 로 마크다운 언어를 사용하여 작성합니다. 마크다운 언어에 대한 사용법은 아래 링크를 참조하세요.  
[마크다운 가이드](/Markdown){:target="_blank"}  

![image](https://user-images.githubusercontent.com/47412229/193743267-6a48645a-ce95-43ce-bc76-45bfe10de48f.png)  

```
---
layout: single
title: "깃허브 페이지 만들기"
---
```
포스팅 레이아웃은 기본적으로 `single` 이며 다양한 레이아웃이 있습니다. 관련 문서는 아래 링크를 참조하세요.  
[POST 레이아웃](https://mmistakes.github.io/minimal-mistakes/docs/layouts/){:target="_blank"}    

`title : "POST 제목"` 블로그에 포스팅한 제목을 설정합니다.  

## 2-5. Site Footer 설정하기 

```
# Site Footer
footer:
  links:
    - label: "Twitter"
      icon: "fab fa-fw fa-twitter-square"
      # url:
    - label: "Facebook"
      icon: "fab fa-fw fa-facebook-square"
      # url:
    - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/kig2929kig"
    - label: "GitLab"
      icon: "fab fa-fw fa-gitlab"
      # url:
    - label: "Bitbucket"
      icon: "fab fa-fw fa-bitbucket"
      # url:
    - label: "Instagram"
      icon: "fab fa-fw fa-instagram"
      # url:
```
  
![image](https://user-images.githubusercontent.com/47412229/193756290-3928b80c-abdd-4d57-bd75-be0c5bdcb4e2.png)


