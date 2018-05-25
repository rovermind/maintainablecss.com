---
layout: chapter
title: ID
section: Background
permalink: /chapters/ids/
description: 스타일링을 위한 ID 사용이 문제를 일으킬 수 있는 이유와 그 대안을 배워봅니다.
---

의미론적으로 말하자면, 어떤 사물의 인스턴스가 단 하나만 존재할 때 ID 를 사용해야 합니다. 그보다 더 많다면 클래스를 사용해야 하겠습니다.

그러나, 우선순위에 의해 [ID 는 클래스를 압도합니다](http://www.w3.org/TR/css3-selectors/#specificity). 이것은 스타일을 덮어쓰고자 할 때 문제가 될 수 있습니다.

이러한 문제를 검증하기 위해, ID 를 이용하여 요소의 컬러를 _빨간색_ 에서 _파란색_ 으로 변경해봅시다.

해당 HTML 입니다:

    <div id="module" class="module-override">

CSS 입니다:

    #module {
      color: red;
    }

    .module-override {
      color: blue;
    }

덮어쓰려는 클래스에 컬러가 파란색이 선언되어 있지만 이 요소의 컬러는 빨간색이 될 것입니다. 이 문제는 ID 선택자를 클래스에 그대로 대입하면 해결됩니다:

    <div class="module module-override">

CSS 입니다:

    .module {
      color: red;
    }

    .module-override {
      color: blue;
    }

이제, 요소의 컬러는 파란색입니다&mdash;문제가 해결되었습니다.

스타일링을 위해 ID 를 사용하는 것은 문제를 내포하고 있지만, 다른 용도로 얼마든지 사용할 수 있습니다. 예를 들면 이런 것들을 매칭해야 할 때 반드시 ID 가 포함됩니다:

* 폼 필드와 레이블
* 페이지 내부의 앵커와 URL 해시값
* 스크린 리더 사용자들을 위한 ARIA 속성

## 결론

브라우저와 기타 보조 기술에 대한 사용자의 특정한 상황이 고려될 경우에만 ID 를 사용하세요. 스타일링을 위한 용도로 사용하는 것은 지양합니다.
