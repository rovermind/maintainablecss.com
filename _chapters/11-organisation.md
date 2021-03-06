---
layout: chapter
title: 구성
section: Extras
permalink: /chapters/organisation/
description: CSS 파일들을 올바르게 구성하는 방법을 배워봅니다.
---

좋은 코드는 탐색하기 쉽고 탐색하기 쉬운 코드는 체계적으로 구성되어 있습니다. 따라서 CSS 도 마찬가지로 잘 구성되기를 바랍니다. 일반적으로 이를 위한 두 가지 방법이 있습니다. 이 장에서는 그 둘을 모두 다룰 것입니다.

## 1. 단일 폴더의 CSS

모든 CSS 를 하나의 폴더 안에 구성하는 경우입니다:

    /path/to/css
      /vendor
        some3rdParty.css
        someOther3rdParty.css
      /yourApp
        some.css
        global.css
        basket.css

### 참고

* 서드파티 CSS 파일들은 `/vendor` 폴더 안에 둡니다.
* 어플리케이션에 포함되는 CSS 파일들은 모두 `/yourApp` 폴더 안에 두며 _yourApp_ 은 당신의 프로젝트 이름입니다.
* 이 방법으로 빌드 스크립트를 통한 번들링과 파일 압축을 위한 디렉토리 타겟팅을 쉽게 할 수 있으며 배포 역시 간단해집니다.
* 가장 흔하게 쓰는 방법이지만 최선은 아닙니다.

## 2. 모듈 폴더의 CSS

이 방식은 모듈과 연관있는 CSS 파일를 자체 폴더 안에 두는 것입니다:

    /global
      /css
        resetPerhaps.css
        global.css
        etc.css
    /basket
      /controllers
        ...
      /templates
        basket.html
        emptyBasket.html
      /partials
        basketHeader.html
        basketSummary.html
      /js
        ...
      /css
        basket.css
    /header
      ...

### 참고

* 보통 기술적인 것보다 기능 지향적인 개발을 하는 경우가 많고, 때문에 이러한 방법은 거의 강제적으로 많이 쓰이고 있습니다.
* 근본적으로 전역 스타일은 모듈에 속하지 않는 것이므로 전역 CSS 는 그 자체의 폴더가 필요합니다.
* 이 방법은 _31 가지 CSS 파일 제한 문제_ 로 어려움을 겪을 수 있습니다. 다음에 이어서 설명합니다.

## 31 가지 CSS 파일 제한 문제

어떤 방식을 택하든, 인터넷 익스플로러에서 발생할 수 있는 31 가지 CSS 파일 제한 문제를 숙지하고 있어야 합니다. 예를 들면 인터넷 익스플로러 9 은 32 번째 파일 (또는 33 번째 등) 에 저장된 스타일을 무시해버립니다.

실제 프로덕션에서는 HTTP 요청을 줄이기 위해 CSS 를 번들링 해야 하므로 괜찮습니다. 그러나 로컬 환경에서는 디버깅을 쉽게 하려면 원래의 소스 파일을 그대로 사용해야 합니다.

만일 로컬 환경에서 **컴파일 단계를 거쳐야 하는 경우에는**&mdash;CSS 프리프로세서를 사용할 때와 같이&mdash;걱정할 필요가 없습니다. 프리프로세서는 파일을 번들링해주기 때문입니다.

만일 로컬 환경에서 **컴파일 단계를 거치지 않는 경우에는**&mdash;소스 파일을 좀 더 쉽게 디버깅하려는&mdash;다음의 두 가지 방식 중 하나로 해결할 수 있습니다:

### 1. 로컬에서만 CSS 를 하나로 모으는 옵션 추가

이렇게 하면 문제를 일으키는 레거시 브라우저에서 CSS 를 디버깅할 수 있고 실제 프로덕션과 유사한 환경을 만들 수 있습니다.

### 2. CSS 파일 갯수는 31 개를 넘지 않게

모듈이 31 개 이상 되어버리면, 모듈 단위의 CSS 를 구성하기는 어려울 일이 될 것입니다. 대신에 동일한 CSS 파일에 여러 모듈의 스타일을 포함시켜야 합니다.

## 최종

이 장에서는 CSS 를 구성하는 두 가지 방식에 대해 알아보았습니다. 이 중 레거시 브라우저와 관련된 31 가지 CSS 파일 제한 문제가 발생할 수 있는 경우를 항상 숙지해야 합니다.
