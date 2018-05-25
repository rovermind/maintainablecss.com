---
layout: chapter
title: 버전관리
section: Extras
permalink: /chapters/versioning/
description: 어떻게 MaintainableCSS 가 빠르게 발전하는 웹사이트의 업그레이드를 쉽게 만드는지 배워봅니다 makes it really easy to upgrade and AB test modules for rapidly evolving websites.
---

예를 들면 모듈의 두 가지 버전에 대한 A/B 테스트를 통해 최선의 대안을 얻으려고 할 수 있습니다. 이렇게 하기 위해, 해당 모듈을 복제한 다음 독자적인 이름을 부여해야 합니다. 예를 들어 두 개의 서로 다른 장바구니를 테스트하려면, CSS 는 다음과 같을 수 있습니다:

    /* 기존의 모듈 (A 유형) */
    .basket {}

    .basket-title {}

    /* 새로운 모듈 (B 유형) */
    .basket2 {}

    .basket2-title {}

이렇게 해서 최선의 결론을 얻을 때까지 테스트에 필요한 두 가지 버전을 유지할 수 있습니다. 이들은 서로 연관성이 전혀 없기 때문에 불필요한 모듈이 생기면 쉽게 제거할 수 있습니다. 좋은 코드는 쉽게 제거할 수 있습니다.
