---
layout: chapter
title: 식별자
section: Core
permalink: /chapters/modifiers/
description: 작은 차이에 기초하여 외형을 바꾸려면 식별자를 사용하세요.
---

상태와 마찬가지로, 식별자 역시 스타일을 덮어씁니다. 모듈(또는 컴포넌트)이 작은 규모이거나 이해하기 쉬운 구조일 때 유용합니다.

각각의 카테고리마다 고유의 배경 이미지를 갖고 있는 헤더가 있는 전자상거래 웹사이트가 있습니다. 모든 헤더는 동일한 마진과 패딩, 그 밖의 값을 가집니다. 유일한 차이는 배경 이미지입니다.

소년 카테고리는 다음과 같은 식별자를 가지고 있습니다:

    <div class="categoryHeader categoryHeader--boys">

비슷하게, 소녀 카테고리는 a _girls_ 식별자를 포함합니다:

    <div class="categoryHeader categoryHeader--girls">

CSS 입니다:

    .categoryHeader {
      padding-top: 50px;
      padding-bottom: 50px;
      /* etc */
    }

    .categoryHeader--boys {
      background-image: url(/path/to/boys.jpg);
    }

    .categoryHeader--girls {
      background-image: url(/path/to/girls.jpg);
    }

차이가 거의 없고 잘 이해할 수 있는 간단한 구조이기 때문에, 이러한 재사용의 형태는 유지보수에 보다 유리합니다.

버튼에 대해서도 동일한 방식으로 접근할 수 있습니다. 대부분의 사이트에는 기본 버튼과 보조 버튼이 있습니다. 만약 하나 혹은 두 개의 스타일에 대한 변경 사항이 있다면 기본 버튼과 보조 버튼에 대한 식별자를 다음과 같이 포함할 수 있습니다:

    .button {
      padding: 20px;
      border-radius: 3px;
      /* etc */
    }

    .button--primary {
      background-color: green;
    }

    .button--secondary {
      background-color: #eee;
    }

다시 말하면, 차이점이 뚜렷하고 이해하기 쉬운 경우에만 효과적입니다.

## 결론

식별자는 잘 이해된 요소 사이의 스타일을 재사용할 수 있는 아주 좋은 방법입니다. 하지만 식별자 자체는 눈에 띄어야 합니다. 만약 오버라이드를 해야 하는 경우가 발생한다면, 식별자는 대안이 되지 못 합니다. 그 대신에 [모듈](/chapters/modules/)을 사용하세요.
