---
layout: single
title: "깃허브 페이지 만들기(2)"
classes: wide
toc : true
toc_sticky: true
categories:
  - 깃허브 페이지 만들기
tags:
  - minimal Mistakes
  - github pages
---

# 깃허브 페이지의  헤더 메뉴 구성하기  
## 1. About 페이지 
깃허브 페이지의 헤더 메뉴 구성은 `_pages` 폴더를 만들고 메뉴에 들어갈 내용의 파일을 작성합니다. 우선, `_data` 폴더의 navigation.yml 파일을 열고 아래와 같이 수정합니다. About 메뉴를 만들고 링크를 설정 후 `_pages` 폴더에 about.md 파일을 작성하면 됩니다.    
  
```
  # main links
  main:
  # - title: "Quick-Start Guide"
  #   url: https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/
  - title: "About"
    url: /about/
  # - title: "Sample Posts"
  #   url: /year-archive/
  # - title: "Sample Collections"
  #   url: /collection-archive/
  # - title: "Sitemap"
  #   url: /sitemap/
```   

![image](https://user-images.githubusercontent.com/47412229/193764827-fa333cb2-02d0-481e-9680-569fd6e3d48a.png)

about.md 파일을 만들때, `permalink: /about/` 추가해야, 링크가 연결됩니다.  

## 2. Tag 페이지  
Tag 헤더 메뉴 또한 `_data` 폴더의 navigation.yml 파일을 열고 아래와 같이 수정합니다.  

```
# main links
main:
  # - title: "Quick-Start Guide"
  #   url: https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/
  - title: "About"
    url: /about/
  - title: "Tag"
    url: /tags/
    
  # - title: "Sample Posts"
  #   url: /year-archive/
  # - title: "Sample Collections"
  #   url: /collection-archive/
  # - title: "Sitemap"
  #   url: /sitemap/
```
`_pages` 폴더에 tag-archive.md 파일을 만들고 내용은 아래 내용을 작성합니다.  

```
---
title: "Posts by Tag"
permalink: /tags/
layout: tags
author_profile: true
---
```  

posting한 파일에 Tag를 추가합니다. `_posts`폴더에 추가한 .md 파일들 중에 Tag를 추가하고 싶은 파일을 선택하여 아래와 같이 편집합니다.

```
---
layout: single
title: "첫번째 블로그입니다."
tags:
  - 블로그
  - blog
---
```

![image](https://user-images.githubusercontent.com/47412229/193958380-398dfe6d-2f44-4ad2-9458-50e995c14ee9.png)

## 3. Category 페이지  
Category 헤더 메뉴도 `_data` 폴더의 navigation.yml 파일을 편집하고 `_pages` 폴더에 category-archive.md 파일을 만듭니다. 그 후 포스팅한 파일들 중에 카테고리를 등록하면 됩니다.

navigation.yml 파일  
```
# main links
main:
  #- title: "Quick-Start Guide"
  # url: https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/
  - title: "About"
    url: /about/
  - title: "Category"
    url: /categories/
  - title: "Tags"
    url: /tags/
```
category-archive.md 파일  
```
---
title: "Posts by Category"
layout: categories
permalink: /categories/
author_profile: true
---
```

`_posts` 폴더에 있는 .md 파일 중 아래 내용처럼 카테고리를 추가합니다.  

```
---
layout: single
title: "첫번째 블로그입니다."
categories:
  - 깃허브 페이지 만들기
tags:
  - 블로그
  - blog
--- 
```

![image](https://user-images.githubusercontent.com/47412229/193960993-d5269eb0-ab0b-4e9f-9ef1-3bae7c275140.png)

