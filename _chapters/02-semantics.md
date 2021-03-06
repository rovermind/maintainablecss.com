---
layout: chapter
title: 의미론적인
section: Background
permalink: /chapters/semantics/
description: 어떻게 보이는지 또는 어떤 상호작용과 연관된 것인지가 아니라 그것이 무엇인지에 따라 작명하는 것은 제대로 설계되고 유지보수할 수 있는 CSS의 기초입니다.
---

의미있는 HTML 은 단지 우리가 직접적으로 사용하는 요소에 관한 것만은 아닙니다. 링크를 나타내기 위해 `<a>` 를 쓰는 것은 꽤 명백한 사실이며, 그 밖에도 테이블 형식의 데이터를 나타내야 할 때에는 `<table>` 을 쓰고 문장은 `<p>` 로 나타냅니다. 그보다 덜 명확한 것이 있다면 우리가 직접 지정하는 클래스명일 것입니다.

Phil Karton 은 “컴퓨터 공학에서 가장 어려운 두 가지가 있다. 바로 캐시 무효화와 **작명**.” 이라고 말 했습니다. 챕터의 대부분을 이와 연관된 내용으로 할애한 것은 매우 적절하게 여겨집니다.

당신이 어떻게 생각할지 모르겠지만 작명은 유지보수할 수 있는 CSS 를 작성하는 방법에 관한 가장 중요한 부분입니다. 두 가지의 주요한 접근 방식이 있습니다: 의미론적인 접근법과 비의미론적인 접근법입니다. 조금 더 자세하게 살펴봅니다.

## 의미론적인 vs 비의미론적인

    <!-- 비의미론적인 -->
    <div class="red pull-left pb3">
    <div class="grid row">
    <div class="col-xs-4">

    <!-- 의미론적인 -->
    <div class="basket">
    <div class="product">
    <div class="searchResults">

비의미론적인 클래스는 요소가 _나타내는 것_ 을 제대로 전달하지 못합니다. 기껏해야 해당 요소가 어떤 모습인지 _보여지는 것_ 에 대한 아이디어만 제공합니다. 요소에 기반하거나, 시각적이고, 상태를 나타내거나, 범용적인 목적으로 고안된 것들 모두 비의미론적인 클래스입니다.

의미론적인 클래스는 요소의 외형적인 스타일을 잘 나타내지 못하지만, 괜찮습니다. 우리에게는 CSS 가 있으니까요. 의미론적인 클래스는 HTML, CSS, 자바스크립트 외 테스트 자동화 등을 모두 수반합니다.

의미론적인 클래스가 더 나은 이유입니다:

## 1. 가독성

다음은 요소에 기반한 클래스를 적용한 HTML 예시입니다:

    <div class="pb3 pb4-ns pt4 pt5-ns mt4 black-70 fl-l w-50-l">
      <h1 class="f4 fw6 f1-ns lh-title measure mt0">Heading</h1>
      <p class="f5 f4-ns fw4 b measure dib-m lh-copy">Tagline</p>
    </div>

* 축약어보다 읽기에 더 좋습니다. 축약어는 사람이 인식할 수 있도록 하는 언어의 특성을 세분화하고 다시 합칩니다. 우리가 당연히 한 번에 그 의미를 알아챌 것이라고 가정한 채 말이죠.
* 거대한 클래스 이름 무더기를 읽는 것은 어려운 일입니다. CSS 가 나름의 문법을 가지고 있는 이유입니다. 우리가 다음과 같은 일들에 대처하려면 수 많은 클래스와 씨름해야 합니다; 무효화되는 클래스; 그리고 특정 브레이크 포인트에서만 적용되는 클래스 등등.
* 이러한 클래스명들은 모호합니다. 예를 들면, `black-70` 은 컬러와 연관된 것일까요? 아니면 배경 색상과 연관된 것일까요? 만약 이를 알아내기 위한 요소 검사를 반드시 해야 한다면, 이 클래스 이름은 바로 알아보기에 어렵다는 사실을 암시하는 것입니다.
* 콘텐츠를 감싸고 있는 HTML 로 인해 그 내용을 알아보기가 어렵습니다.

여기 의미론적인 클래스를 적용한 똑같은 예시가 있습니다:

    <div class="hero">
      <h1 class="hero-title">Heading</h1>
      <p class="hero-tagline">Tagline</p>
    </div>

* 이 클래스 이름들은 읽기 쉽습니다. 이를 이해하려고 머리를 써야 할 필요가 없습니다.
* 콘텐츠는 더 이상 혼동을 주지 않습니다.
* 우리는 모듈이 시작되는 지점과 끝나는 지점을 알 수 있습니다.
* HTML 의 사이즈가 절반으로 줄어들었습니다.
* (요소 검사를 하거나 파일을 직접 살펴보거나) CSS 를 읽기 쉬워졌습니다. 전용 언어이기 때문입니다. constructs that exist for this purpose already.

## 2. 반응형웹 개발에 유리합니다

두 개의 반응형 컬럼을 코딩한다고 상상해 보세요:

* 각 컬럼은 화면 사이즈에 상관없이 `20px` 와 `50px` 의 패딩 값을 가집니다.
* 각 컬럼은 화면 사이즈에 상관없이 `2em` 와 `3em` 의 폰트 사이즈를 가집니다; 동시에
* 컬럼들은 작은 크기의 화면에서 포개집니다. 지금부터 _column_ 은 다소 오해의 여지가 있는 클래스명이라는 사실을 명심하세요.

시각적이고/범용적인 클래스 이름은 다음과 같이 나타낼 수 있습니다:

    <div class="grid clearfix">
      <div class="col pd20 pd50 fs2 fs3">Column 1</div>
      <div class="col pd20 pd50 fs2 fs3">Column 2</div>
    </div>

* 7 개의 클래스 이름이 있습니다, 그 중 일부는 다른 것들을 오버라이드 시킵니다.
* 컬럼들을 실제 반응형에 맞게 만들기 위해 a `fs3large` 라는 다른 클래스 이름이 필요합니다. This means using a naming convention that recreates language constructs already found and standardised in CSS.
* 특정 브레이크 포인트에서, 어떤 클래스는 혼란을 주기도 하고, 불필요한 경우도 발생합니다. 예를 들면 `.clearfix` 는 작은 화면에서 적용되지 않아야 할 수도 있습니다.

A quick evaluation shows significant pain already.

의미론적인 클래스는 다음과 같이 나타냅니다:

    <div class="thing">
      <div class="thing-thingA"></div>
      <div class="thing-thingB"></div>
    </div>

* 이 클래스명들은 모듈의 디자인과 내용에 맞게 캡슐화되었습니다.
* 스타일링 하기 쉽습니다. 다량의 클래스를 작성해야 한다거나, HTML 을 다시 변경하지 않아도 됩니다.
* 이 클래스명들은 작은 화면이나 큰 화면에서나 의미를 가지고 있습니다.
* 미디어쿼리의 사용 여부와 상관 없이 꼭 필요할 때에만 요소를 해제할 수 있습니다.

> 질문: 반응형 그리드 시스템의 중요성은 어느 정도일까요? A [레이아웃은 콘텐츠에 맞게 대응되어야 합니다](http://adamsilver.io/articles/stop-using-device-breakpoints/), 다른 적당한 대안이 없다면 말이죠.

## 3. 찾기 쉽습니다

비의미론적인 클래스를 적용한 HTML 내부를 검색하는 경우 그 검색량은 어마어마합니다. 의미론적인 클래스는 독자적입니다, 하나를 검색하면 오직 하나의 결과만 나올 것입니다, 그러므로 HTMl 을 역추적하는 것이 쉬워집니다.

## 4. 퇴행의 위험성을 제거합니다

시각적인 클래스 이름을 업데이트 하는 것은 여러 요소에 걸쳐 퇴행되는 문제를 일으킬 수 있습니다. 의미론적인 클래스 이름을 업데이트 하는 것은 해당 모듈에만 적용 됩니다, 퇴행의 위험을 전적으로 제거합니다.

## 5. 시각적인 클래스는 도움이 되지 않습니다

어떤 경우에 우리는 인라인 스타일을 쓰기도 합니다. 이는 더욱 명시적이며 CSS 코드가 차지하는 공간을 줄여줍니다. 그럼에도 인라인 CSS 는 문제가 있습니다. 예를 들면 HTML 과 CSS 를 섞어서 쓰는 것은 서로의 관심사를 합쳐버리서 캐시할 수 없기 때문에 미디어 쿼리를 사용할 수 없게 됩니다.

> 질문: `.red` 는 우리가 알고 있는 CSS 에서 제공하는 `color: red` 라는 값을 온전하게 나타낸 것일까요?

## 6. 테스트 자동화에 필요한 훅을 제공합니다

테스트 자동화는 요소를 검색하거나, 상호작용해야 할 경우에 적용합니다. 다음 항목들을 포함합니다:

1.  링크를 클릭하는 경우
2.  텍스트박스를 찾는 경우
3.  텍스트를 타이핑하는 경우
4.  폼을 제출하는 경우
5.  특정 조건에 대한 유효성 검사

특정 요소에만 적용하려는 비의미론적인 클래스를 사용할 수 없습니다. 특히나 특정한 테스트를 위한 훅을 별도로 추가하는 일은 사용자가 이를 다운로드하거나 단계를 거쳐야 하기 때문에 시간낭비에 가깝습니다.

## 7. 자바스크립트 훅을 제공합니다

자바스크립트를 이용한 기능 개선을 할 경우에, 특정 요소에만 적용하려는 비의미론적인 클래스를 사용할 수 없습니다.

## 8. 따로 유지보수할 필요가 없습니다

그것이 무엇인지에 관한 것만을 기준으로 이름을 짓게 되면, 나중에 HTML 을 재작성해야 할 필요가 전혀 없습니다. 예를 들면 헤딩은 언제나 헤딩입니다. 그게 어떤 식으로 _생겼는지_ 여부와는 상관없이 말이죠.

시각적인 클래스를 쓰는 경우, HTML 과 CSS 양쪽 모두 업데이트 해야 합니다. (업데이트에 필요한 사용할 수 있는 선택자가 전혀 없는 경우를 가정한 것입니다).

## 9. 디버깅에 유리합니다

여러 요소 기반의 클래스가 적용된 요소들을 검사한다는 것은, 수 많은 선택자들 사이를 헤쳐나가야 하는 것을 의미합니다. 의미론적인 클래스가 적용되었다면 한 가지만 신경 쓰면 됩니다. 디버깅이 훨씬 더 쉬워집니다.

## 10. 표준입니다

클래스 어트리뷰트를 사용하는 것에 관해, HTML5 스펙에서는 3.2.5.7 조항에서 다음과 같이 밝히고 있습니다:

> "[...] 작성자는 자신이 콘텐츠가 어떻게 보여질지 기대되는 것과 상관 없이, 콘텐츠가 가지고 있는 본래의 성격에 맞는 값을 사용하길 권합니다."

## 11. 상태에 대한 스타일링이 더 쉽습니다

다음 HTML 을 살펴보세요:

    <a class="padding-left-20 red" href="#"></a>

이 경우 호버되었을 때의 패딩과 컬러 값을 변경하는 것은 사실 어려운 일입니다. 이처럼 문제를 일으킬 소지가 있는 경우를 아예 사전에 차단하는 것이 가장 좋습니다.

## 12. HTML 코드량을 줄여줍니다

앞에서 밝힌 것처럼, 요소에 기반한 클래스는 HTML 을 마구 부풀립니다. 의미론적인 클래스는 그보다 훨씬 더 HTML 을 줄일 수 있습니다. 반면에 CSS 사이즈가 늘어날 수는 있겠지만, 이는 캐시가 가능합니다.

## 결론

의미론적인 클래스는 _MaintainableCSS_ 의 주춧돌입니다. 주춧돌이 없으면, 모든 것은 단번에 무너져 버립니다. 단지 그것이 무엇인지에 관한 사실만으로 이름을 지으면 됩니다. 모든 것들은 완벽하게 제자리에 놓일 것입니다.
