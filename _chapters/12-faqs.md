---
layout: chapter
title: FAQ
section: Extras
permalink: /chapters/faqs/
description: MaintainableCSS에 대한 질문과 그 답변입니다.
---

만일 적절한 해답을 찾지 못했을 경우에는, [깃허브에 이슈를 등록해주세요](https://github.com/adamsilver/maintainablecss.com/issues/new). 감사합니다!

## 이 글을 번역할 수 있을까요?

네. 이렇게 하면 됩니다:

1.  [저장소를 포크해주세요](https://github.com/adamsilver/maintainablecss.com/).
2.  당신만의 도메인 (국가 코드) 을 설정해주세요.
3.  출처를 밝히고 제게 알려주세요. :)

<!-- ## When should I use this?

If you like to keep things truly simple, use this approach. It works well if you're building long-lived, bespokely designed, responsive sites that scale and evolve over time. -->

## 헤딩이나 그 밖에 다른 태그의 상속 문제는요?

이상적으로 의미론적인 HTML 은 흠이 없는 비주얼 디자인과 완전히 일치합니다. 모든 `h1` 태그는 동일한 것이라고 여긴다는 의미입니다. 이런 경우 다음과 같이 CSS 를 선언할 수 있습니다:

    h1 {
      /* etc */
    }

하지만, 이것은 전자상거래와 같은 거대한 규모의 웹사이트에서는 극히 드문 경우입니다. 이런 경우에는 해당 모듈에 종속되는 스타일을 캡슐화해야 합니다:

    .module-heading {
      font-size: ...;
      color: ...;
    }

<!--## Where do I put media queries?

The screen should adapt to the content, not the other way around.

This means a module's breakpoints shouldn't be predetermined by *small*, *medium* and *large*. Doing this constrains the design and degrades the user experience.

Therefore, all styles&mdash;even those that are wrapped in media queries&mdash;should be located next to regular styles:

	.basket {}

	@media(min-width: 500px) {
      .basket {}
	}

	@media(min-width: 1000px) {
	  .basket {}
	}

	.basket-heading {}

## Where do I put modifiers and states?

States and modifiers, similarly to media queries, should be located in close proximity to the element they pertain to:

	.basket {}

	.basket-isHidden {}

	.basket-heading {}

	.basket-heading--someModifier {}-->

## 답변을 찾을 수 없나요?

[깃허브에 이슈를 등록해주세요](https://github.com/adamsilver/maintainablecss.com/issues/new). 가능한 빨리 답변을 드리도록 하겠습니다. 감사합니다!
