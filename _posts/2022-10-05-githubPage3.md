---
layout: single
title: "깃허브 페이지 만들기(3)"
classes: wide
toc : true
toc_sticky: true
categories:
  - 깃허브 페이지 만들기
tags:
  - minimal Mistakes
  - github pages
---

# 1. TOC(Table of ContentsPermalink) 설정하기

TOC 기능은 문서의 제목을 목차로 표시해 주며 오른쪽 사이드에 적용됩니다. 설정 방법은 `_posts` 폴더에 있는 적용하고 싶은 파일(.md)을 아래와 같이 편집하면 됩니다.  

```
---
layout : single
title : "TOC 설정 방법"
toc : true
toc_sticky : true
---

# TOC 목차 만들기  
TOC 목차를 만드는 과정입니다.

## 1. toc : true  
설정 방법은 간단합니다. `toc : true` 를 문서에 추가하면 됩니다.

## 2. toc_sticky : true  
`toc_sticky : true` 설정은 TOC 목차를 고정하는 역할을 합니다.

# 3. 마무리  
`#` 을 이용하여 문서의 제목을 작성할 때, 이 부분들이 TOC 목차에 표시됩니다. 
```

![image](https://user-images.githubusercontent.com/47412229/193985548-9e2cf8fe-645a-4cb8-a0b1-ac29e926b698.png)

## 1-1. TOC 제목 변경하기  

TOC의 기본 제목은 "On This Page"이다. TOC의 제목을 변경하는 방법은 `toc_label : "목차" `를 추가하면 됩니다.  

```
---
layout : single
title : "TOC 설정 방법"
toc : true
toc_label : "목차"
toc_sticky : true
---
```  

![image](https://user-images.githubusercontent.com/47412229/193987787-e6e76fbe-e043-421a-9d80-4099b00c7fae.png)  
  
  
# 2. 댓글 기능 추가하기  

utterances는 깃허브 앱(github issue에 사용)으로 깃허브 계정만 있으면 사용할 수 있습니다. 또한, 마크다운 문법을 사용하여 댓글 작성이 가능합니다. 특히, 플랫폼을 변경해도 기존 댓글을 그대로 가져올 수 있습니다.  

## 2-1. github에 새로운 repository를 생성합니다.(댓글을 위한 repo)  
`blog-comments`라는 이름으로 repo를 생성하고 https://github.com/apps/utterances 사이트로 이동합니다. utterances 앱을 install 버튼을 클릭하여 설치를 진행합니다. Only select repositories를 클릭하고 "(github 계정)/blog-comments" 선택합니다. (예, kig29kig/blog-comments) 사이트 하단의 install 버튼을 클릭하여 설치를 종료합니다.  `_config.yml` 파일을 아래와 같이 편집합니다.  


![image](https://user-images.githubusercontent.com/47412229/194020125-2b81a787-ee33-40d4-81ed-28a98bab859a.png)  

```
# breadcrumbs            : false # true, false (default)
words_per_minute         : 200
comments:
  provider               : "utterances" # false (default), "disqus", "discourse", "facebook", "staticman", "staticman_v2", "utterances", "giscus", "custom"
  disqus:
    shortname            : # https://help.disqus.com/customer/portal/articles/466208-what-s-a-shortname-
  discourse:
    server               : # https://meta.discourse.org/t/embedding-discourse-comments-via-javascript/31963 , e.g.: meta.discourse.org
  facebook:
    # https://developers.facebook.com/docs/plugins/comments
    appid                :
    num_posts            : # 5 (default)
    colorscheme          : # "light" (default), "dark"
  utterances:
    theme                : "github-light" # "github-light" (default), "github-dark"
    issue_term           : "pathname" # "pathname" (default)
```
```
# Defaults
defaults:
  # _posts
  - scope:
      path: ""
      type: posts
    values:
      layout: single
      author_profile: true
      read_time: false
      show_date: true
      comments: true # true
      share: true
      related: true
 ```

##  2-2. utterances.html 파일 편집하기
 
`_includes/comments-providers/utterances.html` 파일을 아래와 같이 설정합니다.  
  
  
```
<script>
  'use strict';

  (function() {
    var commentContainer = document.querySelector('#utterances-comments');

    if (!commentContainer) {
      return;
    }

    var script = document.createElement('script');
    script.setAttribute('src', 'https://utteranc.es/client.js');
    script.setAttribute('repo', 'kig29kig/blog-comments');
    script.setAttribute('issue-term', 'pathname');
    script.setAttribute('label', 'blog-comments');
    script.setAttribute('theme', 'github-light');
    script.setAttribute('crossorigin', 'anonymous');

    commentContainer.appendChild(script);
  })();
</script>
```  
  

##  2-3. 댓글 확인  
이제 포스팅된 문서들에 댓글(utterances) 기능이 추가되었느지, 확인 후 댓글을 입력해 봅니다.  

![image](https://user-images.githubusercontent.com/47412229/194022390-d573fb81-90b3-4c7e-9cfe-489c95868e6c.png)

  





