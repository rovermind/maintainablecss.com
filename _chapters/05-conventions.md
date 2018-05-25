---
layout: chapter
title: 규칙
section: Core
permalink: /chapters/conventions/
description: 모듈, 컴포넌트, 그리고 상태를 만들 때 MaintainableCSS 에서 따르는 간단한 규칙을 배워봅니다.
---

_MaintainableCSS_ 는 다음의 규칙을 따릅니다 :

    .<모듈>[-<컴포넌트>][-<상태>] {}

대괄호는 모듈의 상태에 따라 선택 사항입니다. 예시가 있습니다:

    /* 모듈 컨테이너 */
    .searchResults {}

    /* 컴포넌트 */
    .searchResults-heading {}

    /* 상태 */
    .searchResults-isLoading {}

참고:

* 컴포넌트와 상태는 모두 대시로 구분됩니다.
* 네이밍은 로우카멜케이스(lowerCamelCase)로 합니다.
* 선택자들은 모듈명과 관련된 접두사를 가지고 있습니다.

## 모든 요소에 이런 클래스 이름을 지정해야 하나요?

그렇지 않습니다. 원한다면 `.searchResults p` 와 같이 작성할 수도 있습니다. 마크다운을 사용하는 것과 같은 일부 경우에는 이렇게 하는 것이 더 좋을 수 있습니다. 하지만 만약 `p` 가 포함된 모듈이 중첩되는 경우라면 내부 스타일이 그대로 상속되어서 중첩될 수 있다는 점을 명심하세요.

## 왜 모듈 이름과 연관된 접두사를 사용해야 하나요?

좋은 질문입니다. 여기 접두사가 없는 HTML 예시가 있습니다:

    <div class="basket">
      <div class="heading">

CSS 입니다:

    /* 모듈 */
    .basket {}

    /* basket 모듈의 헤딩 컴포넌트 */
    .basket .heading {}

두 가지 문제가 있습니다:

1.  HTML 을 살펴보면, 모듈과 컴포넌트를 서로 분간하기가 어렵습니다; 또한
2.  `.basket .heading` 컴포넌트는 `.heading` 모듈의 스타일을 그대로 상속받게 되고 이는 의도하지 않은 부작용을 일으킬 수 있습니다.
