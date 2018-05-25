---
layout: chapter
title: 자바스크립트
section: Extras
permalink: /chapters/javascript/
description: 유지보수할 수 있는 CSS와 자바스크립트를 동시에 작성하는 방법.
---

여러 모듈이나 컴포넌트 사이의 동일한 상호작용 이벤트를 구현하기 위해 자바스크립트를 이용할 수 있습니다.

예를 들어, 요소의 시각적 상태를 토글하기 위한 `Collapser` 생성자를 사용할 수 있습니다.

우리가 취할 수 있는 두 가지 접근 방식이 있는데, 모두 이전에서 언급한 CSS 를 이용한 접근 방식을 보완할 수 있습니다.

## 1. 모듈의 상태를 캡슐화하기

이를 위해, 다음과 같이 생성자에 대한 모듈의 특정 상태를 나타내는 클래스를 지정해야 합니다:

    var module1Collapser = new Collapser(element1, {
      cssHideClass: 'moduleA-isHidden'
    });

    var module2Collapser = new Collapser(element2, {
      cssHideClass: 'moduleB-isHidden'
    });

CSS 스타일은 다음과 같이 재사용 합니다:

    .moduleA-isHidden,
    .moduleB-isHidden {
      display: none;
    }

위 코드 리스트가 갑작스럽게 늘어난다고 해도 상대적인 균형은 유지됩니다 (믹스인을 사용하는 경우에도 마찬가지입니다). 상호작용이 발생하면 CSS 는 그에 맞게 업데이트 됩니다. 변경되는 부분은 아주 작습니다. 이런 경우에 전역 상태 클래스를 고려할 수 있습니다.

## 2. 전역 상태의 클래스 생성하기

여러 모듈에 대하여 동일한 스타일셋을 적용하기 위한 반복적인 작업을 하고 있다면, 다음처럼 전역 상태와 관련된 클래스 이름을 지정하는 것이 훨씬 더 낫습니다:

    .globalState-isHidden {
      display: none;
    }

이 방식은 앞서 살펴본 코드 리스트를 줄여줍니다. 우리는 이제 더 이상 인스턴스를 생성할 때 모듈의 클래스 이름을 특정해야 할 필요가 없습니다. 전역 클래스가 인스턴스 내부에서 이미 참조되고 있기 때문입니다.

    var module1Collapser = new Collapser(element1);
    var module2Collapser = new Collapser(element2);

하지만, 이러한 방식이 항상 옳은 것은 아닙니다. 동일한 _상호작용_ 을 하지만 _외형_ 은 서로 다른 두 개의 모듈이 존재하는 경우입니다. 우리는 이미 [상태](/chapters/state/) 에서 이 문제를 다룬 바 있습니다.

## 3. 둘 중에 가장 좋은 방법

전역 상태 클래스를 기본 클래스로 설정하는 것으로 두 가지 방식을 결합할 수 있습니다. 그런 다음 필요할 경우에만 앞서 살펴본 첫 번째 예시처럼 인스턴스를 이용해 클래스를 지정할 수 있습니다.

## 결론

상태에 대해, 특히 자바스크립트와 관련된 경우에 그것이 스타일 뿐만 아니라 상호작용에도 영향을 미칠 수 있다는 사실을 명심해야 합니다. 서로 다른 컴포넌트는 동일한 상호작용을 공유하지만, 완전히 다른 모습일 수 있습니다. 이 점을 충분히 고려한 후에 문제에 대한 올바른 대안을 찾을 수 있습니다.

<!-- display: flex vs display: block -->
