---
layout: documentation
title: ReactiveX - Operators
id: operators
---

<h1>연산자 소개</h1>

ReactiveX의 여러 언어 별 구현체들은 다양한 연산자들을 제공한다. 여러 구현체 들 간에는 공통으로 제공하는 것도 있지만 반대로 특정 구현체에서만 제공하는 연산자들도 존재한다.
또한, 각각의 언어별 구현체들은 이미 각 언어에서 제공하는 메서드의 이름과 유사한 형태로 연산자의 이름을 지정하도록 했다.

<h2>연산자 체인</h2>

대부분의 연산자들은 Observable 상에서 동작하고 Observable을 리턴한다. 이런 접근 방법은 연산자들을 연이어서 사용할 수 있는, 연산자 체인을 제공한다. 
연산자 체인에서 각각의 연산자는 이전 연산자가 리턴한 Observable 상에서 동작하며 동작에 따라 그 Observable을 변경시킨다.

뿐만 아니라, 특정 클래스가 제공하는 다양한 메서드 호출을 통해서 그 클래스의 항목들을 변경시키는, 빌더 패턴과 같은 것도 존재한다. 이런 패턴 역시 연산자 체인과 유사한 메서드 체인을 제공한다.
하지만, 빌더 패턴의 경우 메서드 체인을 통해 호출되는 메서드들은 Observable 연산자와는 달리 <em>호출 순서</em>가 실행 결과에 영향을 미치지 않는다.

Observable 연산자 체인은 원본 Observable과 독립적으로 실행될 수 없고 <em>순서대로</em> 실행되어야 한다. 체인에서 먼저 실행된 연산자가 리턴한 Observable을 상에서 바로 다음 연산자가 동작한다.

<h2>ReactiveX의 연산자</h2>

이 페이지에서는 첫 번째로 ReactiveX에서 &ldquo;핵심&rdquo;으로 여겨지는 연산자들을 나열하고, 각 연산자별 링크를 통해서 연산자들이 어떻게 동작하고 ReactiveX의 언어별 구현체에서 이 연산자들이 어떻게 구현했는지를 자세히 설명한다.

그 다음으로 소개하는 내용은 &ldquo;결정 트리&rdquo;로, 여러분이 놓인 상황에서 가장 적합한 연산자를 선택할 수 있도록 가이드하는 아주 유용한 힌트를 제공한다.

마지막으로, ReactiveX의 다양한 언어 별 구현체에서 사용 가능한 모든 연산자들을 알파벳 순으로 소개한다. 또한 이 연산자들 역시 링크를 통해서 언어 별 구현체가 제공하는 연산자와 가장 유사한 핵심 연산자에 대한 설명을 제공한다.
(예를 들어, Rx.NET의 &ldquo;SelectMany&rdquo; 연산자의 링크는 Rx.NET의 SelectMany 연산자가 구현하고 있는 ReactiveX의 <span class="operator">FlatMap</span> 연산자에 대한 자세한 설명을 제공한다)

만약 본인 스스로 연산자를 구현하고 싶다면 <a href="implement-operator.html">연산자 구현하기</a>를 참고하기 바란다.

<h4>내용</h4> 
<ol>
 <li><a href="#categorized">카테고리 별 연산자</a></li>
 <li><a href="#tree">Observable 연산자의 결정 트리</a></li>
 <li><a href="#alphabetical">Observable 연산자 리스트(알파벳순)</a></li>
</ol>

<h1 id="categorized">카테고리 별 연산자</h1>

<h2 id="creating">Observable 생성</h2>

새로운 Observable을 만드는 연산자들

* [**`Create`**]({{ site.url }}/documentation/operators/create.html) — 구현된 옵저버 메서드 호출을 통해 최초 Observable을 생성한다
* [**`Defer`**]({{ site.url }}/documentation/operators/defer.html) — 옵저버가 구독을 하기 전까지는 Observable을 만들지 않고 있다가 구독이 시작되면 옵저버 별로 Observable을 생성한다
* [**`Empty`/`Never`/`Throw`**]({{ site.url }}/documentation/operators/empty-never-throw.html) — 아주 정확하고 제한된 행동을 하는 Observable을 생성한다
* [**`From`**]({{ site.url }}/documentation/operators/from.html) — 다른 객체나 자료 구조를 Observable로 변환한다
* [**`Interval`**]({{ site.url }}/documentation/operators/interval.html) — 특정한 시간 간격별로 연속된 정수형을 발행하는 Observable을 생성한다
* [**`Just`**]({{ site.url }}/documentation/operators/just.html) — 하나 또는 복수 개의 객채들을 Observable로 변환하며 변환된 Observable은 원본 객체들을 발행한다
* [**`Range`**]({{ site.url }}/documentation/operators/range.html) — 범위로 구성된(Range) 정수형을 발행하는 Observable을 생성한다
* [**`Repeat`**]({{ site.url }}/documentation/operators/repeat.html) — 특정 항목이나 연속된 항목들을 반복적으로 배출하는 Observable을 생성한다
* [**`Start`**]({{ site.url }}/documentation/operators/start.html) — 함수의 결과를 발행하는 Observable을 생성한다
* [**`Timer`**]({{ site.url }}/documentation/operators/timer.html) — 주어진 시간 후에 하나의 항목을 배출하는 Observable을 생성한다

<h2 id="transforming">Observable 변환</h2>

Observable이 배출한 항목들을 변환하는 연산자들

* [**`Buffer`**]({{ site.url }}/documentation/operators/buffer.html) — Observable로부터 정기적으로 항목들을 수집한 후 묶음으로 만든 후에 묶음 안에 있는 항목들을 한번에 하나씩 발행하지 않고 수집된 묶음 단위로 발행한다
* [**`FlatMap`**]({{ site.url }}/documentation/operators/flatmap.html) — 하나의 Observable이 발행한 항목들을 복수개의 Observable로 변환 후, 항목들의 배출을 차례차례 줄 세워 하나의 Observable로 전달한다
* [**`GroupBy`**]({{ site.url }}/documentation/operators/groupby.html) — 원본 Observable로부터 키에 해당하는 그룹을 분류시키도록 하나의 Observable을 여러 Observable로 분리시키며 나눠진 Observable은 해당 그룹에 속한 항목들을 배출한다
* [**`Map`**]({{ site.url }}/documentation/operators/map.html) — Observable이 배출한 항목에 함수를 적용시킨다
* [**`Scan`**]({{ site.url }}/documentation/operators/scan.html) — Observable이 배출한 항목에 연속적으로 함수를 적용하고 실행시켜 성공적으로 실행한 값을 발행한다
* [**`Window`**]({{ site.url }}/documentation/operators/window.html) — Observable로부터 항목들을 정기적으로 더 작은 단위의 Observable 윈도우로 나누고 항목을 한번에 하나씩 발행하기 보단 작게 나눠진 윈도우 단위로 발행한다

<h2 id="filtering">Observable 필터링</h2>

소스 Observable에서 선택적으로 항목을 배출하는 연산자들

* [**`Debounce`**]({{ site.url }}/documentation/operators/debounce.html) — 다른 항목들을 배출하지 않은 채 특정 시간이 지났다면 Observable로부터 항목 하나를 배출한다
* [**`Distinct`**]({{ site.url }}/documentation/operators/distinct.html) — Observable로부터 배출된 항목들 중 중복된 항목을 제거한다
* [**`ElementAt`**]({{ site.url }}/documentation/operators/elementat.html) — Obserable로부터 <i>n</i>번째 항목만 배출한다
* [**`Filter`**]({{ site.url }}/documentation/operators/filter.html) — 테스트 조건을 만족하는 항목들만 배출한다
* [**`First`**]({{ site.url }}/documentation/operators/first.html) — 맨 첫 번째 항목 또는 조건을 만족하는 첫 번째 항목만 배출한다
* [**`IgnoreElements`**]({{ site.url }}/documentation/operators/ignoreelements.html) — 항목들을 배출하지는 않지만 종료 알림은 보낸다
* [**`Last`**]({{ site.url }}/documentation/operators/last.html) — Observable로부터 마지막 항목만 배출한다
* [**`Sample`**]({{ site.url }}/documentation/operators/sample.html) — 특정 시간 간격으로 최근에 Observable이 발행한 항목들을 배출한다
* [**`Skip`**]({{ site.url }}/documentation/operators/skip.html) — Observable 발행한 처음 <i>n</i>개의 항목들을 숨긴다
* [**`SkipLast`**]({{ site.url }}/documentation/operators/skiplast.html) — Observable이 발행한 마지막 <i>n</i>개의 항목들을 숨긴다
* [**`Take`**]({{ site.url }}/documentation/operators/take.html) — Observable이 발행한 처음 <i>n</i>개의 항목들만 배출한다
* [**`TakeLast`**]({{ site.url }}/documentation/operators/takelast.html) — Observable이 발행한 마지막 <i>n</i>개의 항목들만 배출한다

<h2 id="combining">Observables 결합</h2>

여러 개의 소스 Observable들을 하나의 Observable로 만드는 연산자들

* [**`And`/`Then`/`When`**]({{ site.url }}/documentation/operators/and-then-when.html) — 두 개 이상의 Observable들이 배출한 항목들을 'Pattern'과 'Plan' 중계자를 이용해서 결합한다
* [**`CombineLatest`**]({{ site.url }}/documentation/operators/combinelatest.html) — 두 개의 Observable 중 하나가 항목을 배출할 때 배출된 맨 마지막 항목을 명시된 함수를 통해 결합하고 이 함수의 결과를 배출한다
* [**`Join`**]({{ site.url }}/documentation/operators/join.html) — A Observable과 B Observable이 배출한 항목들을 결합하는데, 이때 B Observable은 배출한 항목이 타임 윈도우를 가지고 있고 이 타임 윈도우가 열려 있는 동안 A Observable은 항목의 배출을 계속한다. Join 연산자는 B Observable의 항목을 배출하고 배출된 이 항목은 타임 윈도우를 시작하며 그 시간 동안 A Observable은 자신의 항목들을 계속 배출하여 이 두 항목들을 결합한다.
* [**`Merge`**]({{ site.url }}/documentation/operators/merge.html) — 복수 개의 Observable들이 배출하는 항목들을 머지하여 하나의 Observable로 만든다
* [**`StartWith`**]({{ site.url }}/documentation/operators/startwith.html) — 소스 Observable이 항목 배출을 시작하기 전에 배출 순서를 지정할 수 있다.
* [**`Switch`**]({{ site.url }}/documentation/operators/switch.html) — Observable들을 배출하는 Observable을 싱글 Observable로 변환하다. 변환된 싱글 Observable은 변환 전 소스 Observable들이 배출한 항목들을 배출한다
* [**`Zip`**]({{ site.url }}/documentation/operators/zip.html) — 명시된 함수를 통해 여러 Observable들이 배출한 항목들을 결합하고 함수의 실행 결과를 항목으로 배출한다

<h2 id="error">오류 처리 연산자</h2>

Observable이 던진 오류를 복구할 수 있도록 도와주는 연산자들

* [**`Catch`**]({{ site.url }}/documentation/operators/catch.html) — 오류를 제외하고 연속된 발행을 계속 진행시켜 'onError'로부터 전달된 오류를 복구한다
* [**`Retry`**]({{ site.url }}/documentation/operators/retry.html) — 만약 소스 Observable이 'onError' 알림을 보낼 경우, 오류 없이 실행이 완료되기를 기대하며 재구독을 시도한다

<h2 id="utility">Observable 유틸리티 연산자</h2>

Obserable과 함께 동작하는 유용한 도우미 연산자들

* [**`Delay`**]({{ site.url }}/documentation/operators/delay.html) — Observable의 배출을 특정 시간 만큼 뒤로 미룬다
* [**`Do`**]({{ site.url }}/documentation/operators/do.html) — Observable의 생명주기 동안 발생하는 다양한 이벤트에서 실행 될 액션을 등록한다
* [**`Materialize`/`Dematerialize`**]({{ site.url }}/documentation/operators/materialize-dematerialize.html) — 배출된 항목과 전달된 알림의 메타 정보를 제공하거나 반대로 메타정보로 항목과 알림을 배출한다
* [**`ObserveOn`**]({{ site.url }}/documentation/operators/observeon.html) — 옵저버가 Observable을 관찰할 스케줄러를 명시한다
* [**`Serialize`**]({{ site.url }}/documentation/operators/serialize.html) — Observable이 직렬화된 호출을 생성해서 제대로 동작하도록 강제한다
* [**`Subscribe`**]({{ site.url }}/documentation/operators/subscribe.html) — Observable이 배출하는 항목과 알림 위에서 동작한다
* [**`SubscribeOn`**]({{ site.url }}/documentation/operators/subscribeon.html) — Observable이 구독될 때 Observable이 사용할 스케줄러를 명시한다
* [**`TimeInterval`**]({{ site.url }}/documentation/operators/timeinterval.html) — convert an Observable that emits items into one that emits indications of the amount of time elapsed between those emissions
* [**`Timeout`**]({{ site.url }}/documentation/operators/timeout.html) — mirror the source Observable, but issue an error notification if a particular period of time elapses without any emitted items
* [**`Timestamp`**]({{ site.url }}/documentation/operators/timestamp.html) — attach a timestamp to each item emitted by an Observable
* [**`Using`**]({{ site.url }}/documentation/operators/using.html) — create a disposable resource that has the same lifespan as the Observable

<h2 id="conditional">Conditional and Boolean Operators</h2>

Operators that evaluate one or more Observables or items emitted by Observables

* [**`All`**]({{ site.url }}/documentation/operators/all.html) — determine whether all items emitted by an Observable meet some criteria
* [**`Amb`**]({{ site.url }}/documentation/operators/amb.html) — given two or more source Observables, emit all of the items from only the first of these Observables to emit an item
* [**`Contains`**]({{ site.url }}/documentation/operators/contains.html) — determine whether an Observable emits a particular item or not
* [**`DefaultIfEmpty`**]({{ site.url }}/documentation/operators/defaultifempty.html) — emit items from the source Observable, or a default item if the source Observable emits nothing
* [**`SequenceEqual`**]({{ site.url }}/documentation/operators/sequenceequal.html) — determine whether two Observables emit the same sequence of items
* [**`SkipUntil`**]({{ site.url }}/documentation/operators/skipuntil.html) — discard items emitted by an Observable until a second Observable emits an item
* [**`SkipWhile`**]({{ site.url }}/documentation/operators/skipwhile.html) — discard items emitted by an Observable until a specified condition becomes false
* [**`TakeUntil`**]({{ site.url }}/documentation/operators/takeuntil.html) — discard items emitted by an Observable after a second Observable emits an item or terminates
* [**`TakeWhile`**]({{ site.url }}/documentation/operators/takewhile.html) — discard items emitted by an Observable after a specified condition becomes false

<h2 id="mathematical">Mathematical and Aggregate Operators</h2>

Operators that operate on the entire sequence of items emitted by an Observable

* [**`Average`**]({{ site.url }}/documentation/operators/average.html) — calculates the average of numbers emitted by an Observable and emits this average
* [**`Concat`**]({{ site.url }}/documentation/operators/concat.html) — emit the emissions from two or more Observables without interleaving them
* [**`Count`**]({{ site.url }}/documentation/operators/count.html) — count the number of items emitted by the source Observable and emit only this value
* [**`Max`**]({{ site.url }}/documentation/operators/max.html) — determine, and emit, the maximum-valued item emitted by an Observable
* [**`Min`**]({{ site.url }}/documentation/operators/min.html) — determine, and emit, the minimum-valued item emitted by an Observable
* [**`Reduce`**]({{ site.url }}/documentation/operators/reduce.html) — apply a function to each item emitted by an Observable, sequentially, and emit the final value
* [**`Sum`**]({{ site.url }}/documentation/operators/sum.html) — calculate the sum of numbers emitted by an Observable and emit this sum

<h2 id="backpressure">Backpressure Operators</h2>

* [**backpressure operators**]({{ site.url }}/documentation/operators/backpressure.html) — strategies for coping with Observables that produce items more rapidly than their observers consume them

<h2 id="connectable">Connectable Observable Operators</h2>

Specialty Observables that have more precisely-controlled subscription dynamics

* [**`Connect`**]({{ site.url }}/documentation/operators/connect.html) — instruct a connectable Observable to begin emitting items to its subscribers
* [**`Publish`**]({{ site.url }}/documentation/operators/publish.html) — convert an ordinary Observable into a connectable Observable
* [**`RefCount`**]({{ site.url }}/documentation/operators/refcount.html) — make a Connectable Observable behave like an ordinary Observable
* [**`Replay`**]({{ site.url }}/documentation/operators/replay.html) — ensure that all observers see the same sequence of emitted items, even if they subscribe after the Observable has begun emitting items

<h2 id="conversion">Operators to Convert Observables</h2>

* [**`To`**]({{ site.url }}/documentation/operators/to.html) — convert an Observable into another object or data structure

<div id="tree">
<style>
   div#tree dl { margin-top: 0;
                 margin-bottom: 1.5em;
                 margin-left: 1.5em; }
   div#tree dl#outer>dt { font-weight: bold;
                          margin-right: -1.5em;
                          margin-top: .5em; }
   div#tree dl#outer>dd { margin-top: .5em; }
   div#tree dt { font-weight: normal;
                 margin-right: -1.5em; }
   div#tree dl > dt::before { content: "…"; }
   div#tree dl#outer > dt::before { content: ""; }
   div#tree dd::before { content: ": "; }
   div#tree dd.sub::before { content: ""; }

   div#tree dt { float: left; clear: left; }
   div#tree dd { float: left;
                 margin-start: 0;
                 -webkit-margin-start: 0;
                 margin-left: 1.5em; }
   div#tree dd.sub { float: none;
                     margin-left: 0; }
</style>
  <h1>Observable 연산자 결정 트리</h1>
  <p>
   This tree can help you find the ReactiveX Observable operator you&#8217;re looking for.
  </p>
<dl id="outer">
 <dt>I want to create a new Observable</dt>
  <dd class="sub"><dl>
   <dt>that emits a particular item</dt>
    <dd><a href="operators/just.html">Just</a></dd>
    <dd class="sub"><dl>
     <dt>that was returned from a function called at subscribe-time</dt>
      <dd><a href="operators/start.html">Start</a></dd>
     <dt>that was returned from an <code>Action</code>, <code>Callable</code>, <code>Runnable</code>, or something of that sort, called at subscribe-time</dt>
      <dd><a href="operators/from.html">From</a></dd>
     <dt>after a specified delay</dt>
      <dd><a href="operators/timer.html">Timer</a></dd>
     </dl></dd>
   <dt>that pulls its emissions from a particular <code>Array</code>, <code>Iterable</code>, or something like that</dt>
    <dd><a href="operators/from.html">From</a></dd>
   <dt>by retrieving it from a Future</dt>
    <dd><a href="operators/start.html">Start</a></dd>
   <dt>that obtains its sequence from a Future</dt>
    <dd><a href="operators/from.html">From</a></dd>
   <dt>that emits a sequence of items repeatedly</dt>
    <dd><a href="operators/repeat.html">Repeat</a></dd>
   <dt>from scratch, with custom logic</dt>
    <dd><a href="operators/create.html">Create</a></dd>
   <dt>for each observer that subscribes</dt>
    <dd><a href="operators/defer.html">Defer</a></dd>
   <dt>that emits a sequence of integers</dt>
    <dd><a href="operators/range.html">Range</a></dd>
    <dd class="sub"><dl>
     <dt>at particular intervals of time</dt>
      <dd><a href="operators/interval.html">Interval</a></dd>
      <dd class="sub"><dl>
       <dt>after a specified delay</dt>
       <dd><a href="operators/timer.html">Timer</a></dd>
      </dl></dd>
    </dl></dd>
   <dt>that completes without emitting items</dt>
    <dd><a href="operators/empty-never-throw.html">Empty</a></dd>
   <dt>that does nothing at all</dt>
    <dd><a href="operators/empty-never-throw.html">Never</a></dd>
  </dl></dd>

 <dt>I want to create an Observable by combining other Observables</dt>
  <dd class="sub"><dl>
   <dt>and emitting all of the items from all of the Observables in whatever order they are received</dt>
    <dd><a href="operators/merge.html">Merge</a></dd>
   <dt>and emitting all of the items from all of the Observables, one Observable at a time</dt>
    <dd><a href="operators/concat.html">Concat</a></dd>
   <dt>by combining the items from two or more Observables sequentially to come up with new items to emit</dt>
    <dd class="sub"><dl>
     <dt>whenever <em>each</em> of the Observables has emitted a new item</dt>
      <dd><a href="operators/zip.html">Zip</a></dd>
     <dt>whenever <em>any</em> of the Observables has emitted a new item</dt>
      <dd><a href="operators/combinelatest.html">CombineLatest</a></dd>
     <dt>whenever an item is emitted by one Observable in a window defined by an item emitted by another</dt>
      <dd><a href="operators/join.html">Join</a></dd>
     <dt>by means of <code>Pattern</code> and <code>Plan</code> intermediaries</dt>
      <dd><a href="operators/and-then-when.html">And/Then/When</a></dd>
    </dl></dd>
   <dt>and emitting the items from only the most-recently emitted of those Observables</dt>
    <dd><a href="operators/switch.html">Switch</a></dd>
  </dl></dd>

 <dt>I want emit the items from an Observable after transforming them</dt>
  <dd class="sub"><dl>
   <dt>one at a time with a function</dt>
    <dd><a href="operators/map.html">Map</a></dd>
   <dt>by emitting all of the items emitted by corresponding Observables</dt>
    <dd><a href="operators/flatmap.html">FlatMap</a></dd>
    <dd class="sub"><dl>
     <dt>one Observable at a time, in the order they are emitted</dt>
      <dd><a href="operators/flatmap.html">ConcatMap</a></dd>
    </dl></dd>
   <dt>based on all of the items that preceded them</dt>
    <dd><a href="operators/scan.html">Scan</a></dd>
   <dt>by attaching a timestamp to them</dt>
    <dd><a href="operators/timestamp.html">Timestamp</a></dd>
   <dt>into an indicator of the amount of time that lapsed before the emission of the item</dt>
    <dd><a href="operators/timeinterval.html">TimeInterval</a></dd>
  </dl></dd>

 <dt>I want to shift the items emitted by an Observable forward in time before reemitting them</dt>
  <dd><a href="operators/delay.html">Delay</a></dd>

 <dt>I want to transform items <em>and</em> notifications from an Observable into items and reemit them</dt>
  <dd class="sub"><dl>
   <dt>by wrapping them in <code>Notification</code> objects</dt>
    <dd><a href="operators/materialize-dematerialize.html">Materialize</a></dd>
    <dd class="sub"><dl>
     <dt>which I can then unwrap again with</dt>
      <dd><a href="operators/materialize-dematerialize.html">Dematerialize</a></dd>
    </dl></dd>
  </dl></dd>

 <dt>I want to ignore all items emitted by an Observable and only pass along its completed/error notification</dt>
  <dd><a href="operators/ignoreelements.html">IgnoreElements</a></dd>

 <dt>I want to mirror an Observable but prefix items to its sequence</dt>
  <dd><a href="operators/startwith.html">StartWith</a></dd>
  <dd class="sub"><dl>
   <dt>only if its sequence is empty</dt>
    <dd><a href="operators/defaultifempty.html">DefaultIfEmpty</a></dd>
  </dl></dd>

 <dt>I want to collect items from an Observable and reemit them as buffers of items</dt>
  <dd><a href="operators/buffer.html">Buffer</a></dd>
  <dd class="sub"><dl>
   <dt>containing only the last items emitted</dt>
    <dd><a href="operators/takelast.html">TakeLastBuffer</a></dd>
  </dl></dd>

 <dt>I want to split one Observable into multiple Observables</dt>
  <dd><a href="operators/window.html">Window</a></dd>
  <dd class="sub"><dl>
   <dt>so that similar items end up on the same Observable</dt>
    <dd><a href="operators/groupby.html">GroupBy</a></dd>
  </dl></dd>

 <dt>I want to retrieve a particular item emitted by an Observable:</dt>
  <dd class="sub"><dl>
   <dt>the last item emitted before it completed</dt>
    <dd><a href="operators/last.html">Last</a></dd>
   <dt>the sole item it emitted</dt>
    <dd><a href="operators/first.html">Single</a></dd>
   <dt>the first item it emitted</dt>
    <dd><a href="operators/first.html">First</a></dd>
  </dl></dd>

 <dt>I want to reemit only certain items from an Observable</dt>
  <dd class="sub"><dl>
   <dt>by filtering out those that do not match some predicate</dt>
    <dd><a href="operators/filter.html">Filter</a></dd>
   <dt>that is, only the first item</dt>
    <dd><a href="operators/first.html">First</a></dd>
   <dt>that is, only the first item<em>s</em></dt>
    <dd><a href="operators/take.html">Take</a></dd>
   <dt>that is, only the last item</dt>
    <dd><a href="operators/last.html">Last</a></dd>
   <dt>that is, only item <i>n</i></dt>
    <dd><a href="operators/elementat.html">ElementAt</a></dd>
   <dt>that is, only those items after the first items</dt>
    <dd class="sub"><dl>
     <dt>that is, after the first <i>n</i> items</dt>
      <dd><a href="operators/skip.html">Skip</a></dd>
     <dt>that is, until one of those items matches a predicate</dt>
      <dd><a href="operators/skipwhile.html">SkipWhile</a></dd>
     <dt>that is, after an initial period of time</dt>
      <dd><a href="operators/skip.html">Skip</a></dd>
     <dt>that is, after a second Observable emits an item</dt>
      <dd><a href="operators/skipuntil.html">SkipUntil</a></dd>
    </dl></dd>
   <dt>that is, those items except the last items</dt>
    <dd class="sub"><dl>
     <dt>that is, except the last <i>n</i> items</dt>
      <dd><a href="operators/skiplast.html">SkipLast</a></dd>
     <dt>that is, until one of those items matches a predicate</dt>
      <dd><a href="operators/takewhile.html">TakeWhile</a></dd>
     <dt>that is, except items emitted during a period of time before the source completes</dt>
      <dd><a href="operators/skiplast.html">SkipLast</a></dd>
     <dt>that is, except items emitted after a second Observable emits an item</dt>
      <dd><a href="operators/takeuntil.html">TakeUntil</a></dd>
    </dl></dd>
   <dt>by sampling the Observable periodically</dt>
    <dd><a href="operators/sample.html">Sample</a></dd>
   <dt>by only emitting items that are not followed by other items within some duration</dt>
    <dd><a href="operators/debounce.html">Debounce</a></dd>
   <dt>by suppressing items that are duplicates of already-emitted items</dt>
    <dd><a href="operators/distinct.html">Distinct</a></dd>
    <dd class="sub"><dl>
     <dt>if they immediately follow the item they are duplicates of</dt>
      <dd><a href="operators/distinct.html">DistinctUntilChanged</a></dd>
    </dl></dd>
   <dt>by delaying my subscription to it for some time after it begins emitting items</dt>
    <dd><a href="operators/delay.html">DelaySubscription</a></dd>
  </dl></dd>

 <dt>I want to reemit items from an Observable only on condition that it was the first of a collection of Observables to emit an item</dt>
  <dd><a href="operators/amb.html">Amb</a></dd>

 <dt>I want to evaluate the entire sequence of items emitted by an Observable</dt>
  <dd class="sub"><dl>
   <dt>and emit a single boolean indicating if <em>all</em> of the items pass some test</dt>
    <dd><a href="operators/all.html">All</a></dd>
   <dt>and emit a single boolean indicating if the Observable emitted <em>any</em> item (that passes some test)</dt>
    <dd><a href="operators/contains.html">Contains</a></dd>
   <dt>and emit a single boolean indicating if the Observable emitted <em>no</em> items</dt>
    <dd><a href="operators/contains.html">IsEmpty</a></dd>
   <dt>and emit a single boolean indicating if the sequence is identical to one emitted by a second Observable</dt>
    <dd><a href="operators/sequenceequal.html">SequenceEqual</a></dd>
   <dt>and emit the average of all of their values</dt>
    <dd><a href="operators/average.html">Average</a></dd>
   <dt>and emit the sum of all of their values</dt>
    <dd><a href="operators/sum.html">Sum</a></dd>
   <dt>and emit a number indicating how many items were in the sequence</dt>
    <dd><a href="operators/count.html">Count</a></dd>
   <dt>and emit the item with the maximum value</dt>
    <dd><a href="operators/max.html">Max</a></dd>
   <dt>and emit the item with the minimum value</dt>
    <dd><a href="operators/min.html">Min</a></dd>
   <dt>by applying an aggregation function to each item in turn and emitting the result</dt>
    <dd><a href="operators/scan.html">Scan</a></dd>
  </dl></dd>

 <dt>I want to convert the entire sequence of items emitted by an Observable into some other data structure</dt>
  <dd><a href="operators/to.html">To</a></dd>

 <dt>I want an operator to operate on a particular <a href="../scheduler.html">Scheduler</a></dt>
  <dd><a href="operators/subscribeon.html">SubscribeOn</a></dd>
  <dd class="sub"><dl>
   <dt>when it notifies observers</dt>
    <dd><a href="operators/observeon.html">ObserveOn</a></dd>
  </dl></dd>

 <dt>I want an Observable to invoke a particular action when certain events occur</dt>
  <dd><a href="operators/do.html">Do</a></dd>

 <dt>I want an Observable that will notify observers of an error</dt>
  <dd><a href="operators/empty-never-throw.html">Throw</a></dd>
  <dd class="sub"><dl>
   <dt>if a specified period of time elapses without it emitting an item</dt>
    <dd><a href="operators/timeout.html">Timeout</a></dd>
  </dl></dd>

 <dt>I want an Observable to recover gracefully</dt>
  <dd class="sub"><dl>
   <dt>from a timeout by switching to a backup Observable</dt>
    <dd><a href="operators/timeout.html">Timeout</a></dd>
   <dt>from an upstream error notification</dt>
    <dd><a href="operators/catch.html">Catch</a></dd>
    <dd class="sub"><dl>
     <dt>by attempting to resubscribe to the upstream Observable</dt>
      <dd><a href="operators/retry.html">Retry</a></dd>
    </dl></dd>
  </dl></dd>

 <dt>I want to create a resource that has the same lifespan as the Observable</dt>
  <dd><a href="operators/using.html">Using</a></dd>

 <dt>I want to subscribe to an Observable and receive a <code>Future</code> that blocks until the Observable completes</dt>
  <dd><a href="operators/start.html">Start</a></dd>

 <dt>I want an Observable that does not start emitting items to subscribers until asked</dt>
  <dd><a href="operators/publish.html">Publish</a></dd>
  <dd class="sub"><dl>
   <dt>and then only emits the last item in its sequence</dt>
    <dd><a href="operators/publish.html">PublishLast</a></dd>
   <dt>and then emits the complete sequence, even to those who subscribe after the sequence has begun</dt>
    <dd><a href="operators/replay.html">Replay</a></dd>
   <dt>but I want it to go away once all of its subscribers unsubscribe</dt>
    <dd><a href="operators/refcount.html">RefCount</a></dd>
   <dt>and then I want to ask it to start</dt>
    <dd><a href="operators/connect.html">Connect</a></dd>
  </dl></dd>
</dl>
</div>
<h4 style="clear:both;">See Also</h4>
<ul>
 <li><a href="http://xgrommx.github.io/rx-book/content/which_operator_do_i_use/index.html">Which Operator do I use?</a> by Dennis Stoyanov (a similar decision tree, specific to RxJS operators)</li>
</ul>

<h1 id="alphabetical" style="clear: left;">Observable 연산자 리스트(알파벳순)</h1>

Canonical, core operator names are in **boldface**. Other entries represent language-specific
variants of these operators or specialty operators outside of the main ReactiveX core set of
operators.

* [`Aggregate`]({{ site.url }}/documentation/operators/reduce.html)
* [**`All`**]({{ site.url }}/documentation/operators/all.html)
* [**`Amb`**]({{ site.url }}/documentation/operators/amb.html)
* [`and_`]({{ site.url }}/documentation/operators/and-then-when.html)
* [**`And`**]({{ site.url }}/documentation/operators/and-then-when.html)
* [`Any`]({{ site.url }}/documentation/operators/contains.html)
* [`apply`]({{ site.url }}/documentation/operators/create.html)
* [`as_blocking`]({{ site.url }}/documentation/operators/to.html)
* [`asObservable`]({{ site.url }}/documentation/operators/from.html)
* [`AssertEqual`]({{ site.url }}/documentation/operators/sequenceequal.html)
* [`asyncAction`]({{ site.url }}/documentation/operators/start.html)
* [`asyncFunc`]({{ site.url }}/documentation/operators/start.html)
* [**`Average`**]({{ site.url }}/documentation/operators/average.html)
* [`averageDouble`]({{ site.url }}/documentation/operators/average.html)
* [`averageFloat`]({{ site.url }}/documentation/operators/average.html)
* [`averageInteger`]({{ site.url }}/documentation/operators/average.html)
* [`averageLong`]({{ site.url }}/documentation/operators/average.html)
* [`blocking`]({{ site.url }}/documentation/operators/to.html)
* [**`Buffer`**]({{ site.url }}/documentation/operators/buffer.html)
* [`bufferWithCount`]({{ site.url }}/documentation/operators/buffer.html)
* [`bufferWithTime`]({{ site.url }}/documentation/operators/buffer.html)
* [`bufferWithTimeOrCount`]({{ site.url }}/documentation/operators/buffer.html)
* [`byLine`]({{ site.url }}/documentation/operators/map.html)
* [`cache`]({{ site.url }}/documentation/operators/replay.html)
* [`case`]({{ site.url }}/documentation/operators/defer.html)
* [`Cast`]({{ site.url }}/documentation/operators/map.html)
* [**`Catch`**]({{ site.url }}/documentation/operators/catch.html)
* [`catchError`]({{ site.url }}/documentation/operators/catch.html)
* [`catchException`]({{ site.url }}/documentation/operators/catch.html)
* [`collect`]({{ site.url }}/documentation/operators/reduce.html)
* [`collect`]({{ site.url }}/documentation/operators/filter.html) (RxScala version of **`Filter`**)
* [**`CombineLatest`**]({{ site.url }}/documentation/operators/combinelatest.html)
* [`combineLatestWith`]({{ site.url }}/documentation/operators/combinelatest.html)
* [**`Concat`**]({{ site.url }}/documentation/operators/concat.html)
* [`concat_all`]({{ site.url }}/documentation/operators/flatmap.html)
* [`concatMap`]({{ site.url }}/documentation/operators/flatmap.html)
* [`concatMapObserver`]({{ site.url }}/documentation/operators/flatmap.html)
* [`concatMapTo`]({{ site.url }}/documentation/operators/flatmap.html)
* [`concatAll`]({{ site.url }}/documentation/operators/concat.html)
* [`concatWith`]({{ site.url }}/documentation/operators/concat.html)
* [**`Connect`**]({{ site.url }}/documentation/operators/connect.html)
* [`connect_forever`]({{ site.url }}/documentation/operators/connect.html)
* [`cons`]({{ site.url }}/documentation/operators/startwith.html)
* [**`Contains`**]({{ site.url }}/documentation/operators/contains.html)
* [`controlled`]({{ site.url }}/documentation/operators/backpressure.html)
* [**`Count`**]({{ site.url }}/documentation/operators/count.html)
* [`countLong`]({{ site.url }}/documentation/operators/count.html)
* [**`Create`**]({{ site.url }}/documentation/operators/create.html)
* [`cycle`]({{ site.url }}/documentation/operators/repeat.html)
* [**`Debounce`**]({{ site.url }}/documentation/operators/debounce.html)
* [`decode`]({{ site.url }}/documentation/operators/from.html)
* [**`DefaultIfEmpty`**]({{ site.url }}/documentation/operators/defaultifempty.html)
* [**`Defer`**]({{ site.url }}/documentation/operators/defer.html)
* [`deferFuture`]({{ site.url }}/documentation/operators/start.html)
* [**`Delay`**]({{ site.url }}/documentation/operators/delay.html)
* [`delaySubscription`]({{ site.url }}/documentation/operators/delay.html)
* [`delayWithSelector`]({{ site.url }}/documentation/operators/delay.html)
* [**`Dematerialize`**]({{ site.url }}/documentation/operators/materialize-dematerialize.html)
* [**`Distinct`**]({{ site.url }}/documentation/operators/distinct.html)
* [`distinctKey`]({{ site.url }}/documentation/operators/distinct.html)
* [`distinctUntilChanged`]({{ site.url }}/documentation/operators/distinct.html)
* [`distinctUntilKeyChanged`]({{ site.url }}/documentation/operators/distinct.html)
* [**`Do`**]({{ site.url }}/documentation/operators/do.html)
* [`doAction`]({{ site.url }}/documentation/operators/do.html)
* [`doAfterTerminate`]({{ site.url }}/documentation/operators/do.html)
* [`doOnCompleted`]({{ site.url }}/documentation/operators/do.html)
* [`doOnEach`]({{ site.url }}/documentation/operators/do.html)
* [`doOnError`]({{ site.url }}/documentation/operators/do.html)
* [`doOnRequest`]({{ site.url }}/documentation/operators/do.html)
* [`doOnSubscribe`]({{ site.url }}/documentation/operators/do.html)
* [`doOnTerminate`]({{ site.url }}/documentation/operators/do.html)
* [`doOnUnsubscribe`]({{ site.url }}/documentation/operators/do.html)
* [`doseq`]({{ site.url }}/documentation/operators/subscribe.html)
* [`doWhile`]({{ site.url }}/documentation/operators/repeat.html)
* [`drop`]({{ site.url }}/documentation/operators/skip.html)
* [`dropRight`]({{ site.url }}/documentation/operators/skiplast.html)
* [`dropUntil`]({{ site.url }}/documentation/operators/skipuntil.html)
* [`dropWhile`]({{ site.url }}/documentation/operators/skipwhile.html)
* [**`ElementAt`**]({{ site.url }}/documentation/operators/elementat.html)
* [`ElementAtOrDefault`]({{ site.url }}/documentation/operators/elementat.html)
* [**`Empty`**]({{ site.url }}/documentation/operators/empty-never-throw.html)
* [`emptyObservable`]({{ site.url }}/documentation/operators/empty-never-throw.html)
* [`empty?`]({{ site.url }}/documentation/operators/contains.html)
* [`encode`]({{ site.url }}/documentation/operators/map.html)
* [`ensures`]({{ site.url }}/documentation/operators/do.html)
* [`error`]({{ site.url }}/documentation/operators/empty-never-throw.html)
* [`every`]({{ site.url }}/documentation/operators/all.html)
* [`exclusive`]({{ site.url }}/documentation/operators/switch.html)
* [`exists`]({{ site.url }}/documentation/operators/contains.html)
* [`expand`]({{ site.url }}/documentation/operators/flatmap.html)
* [`failWith`]({{ site.url }}/documentation/operators/empty-never-throw.html)
* [**`Filter`**]({{ site.url }}/documentation/operators/filter.html)
* [`filterNot`]({{ site.url }}/documentation/operators/filter.html)
* [`Finally`]({{ site.url }}/documentation/operators/do.html)
* [`finallyAction`]({{ site.url }}/documentation/operators/do.html)
* [`finallyDo`]({{ site.url }}/documentation/operators/do.html)
* [`find`]({{ site.url }}/documentation/operators/contains.html)
* [`findIndex`]({{ site.url }}/documentation/operators/contains.html)
* [**`First`**]({{ site.url }}/documentation/operators/first.html)
* [`FirstOrDefault`]({{ site.url }}/documentation/operators/first.html)
* [`firstOrElse`]({{ site.url }}/documentation/operators/first.html)
* [**`FlatMap`**]({{ site.url }}/documentation/operators/flatmap.html)
* [`flatMapFirst`]({{ site.url }}/documentation/operators/flatmap.html)
* [`flatMapIterable`]({{ site.url }}/documentation/operators/flatmap.html)
* [`flatMapIterableWith`]({{ site.url }}/documentation/operators/flatmap.html)
* [`flatMapLatest`]({{ site.url }}/documentation/operators/flatmap.html)
* [`flatMapObserver`]({{ site.url }}/documentation/operators/flatmap.html)
* [`flatMapWith`]({{ site.url }}/documentation/operators/flatmap.html)
* [`flatMapWithMaxConcurrent`]({{ site.url }}/documentation/operators/flatmap.html)
* [`flat_map_with_index`]({{ site.url }}/documentation/operators/flatmap.html)
* [`flatten`]({{ site.url }}/documentation/operators/merge.html)
* [`flattenDelayError`]({{ site.url }}/documentation/operators/merge.html)
* [`foldl`]({{ site.url }}/documentation/operators/reduce.html)
* [`foldLeft`]({{ site.url }}/documentation/operators/reduce.html)
* [`for`]({{ site.url }}/documentation/operators/flatmap.html)
* [`forall`]({{ site.url }}/documentation/operators/all.html)
* [`ForEach`]({{ site.url }}/documentation/operators/subscribe.html)
* [`forEachFuture`]({{ site.url }}/documentation/operators/start.html)
* [`forIn`]({{ site.url }}/documentation/operators/flatmap.html)
* [`forkJoin`]({{ site.url }}/documentation/operators/zip.html)
* [**`From`**]({{ site.url }}/documentation/operators/from.html)
* [`fromAction`]({{ site.url }}/documentation/operators/from.html)
* [`fromArray`]({{ site.url }}/documentation/operators/from.html)
* [`FromAsyncPattern`]({{ site.url }}/documentation/operators/from.html)
* [`fromCallable`]({{ site.url }}/documentation/operators/from.html)
* [`fromCallback`]({{ site.url }}/documentation/operators/from.html)
* [`FromEvent`]({{ site.url }}/documentation/operators/from.html)
* [`FromEventPattern`]({{ site.url }}/documentation/operators/from.html)
* [`fromFunc0`]({{ site.url }}/documentation/operators/from.html)
* [`from_future`]({{ site.url }}/documentation/operators/from.html)
* [`from_iterable`]({{ site.url }}/documentation/operators/from.html)
* [`fromIterator`]({{ site.url }}/documentation/operators/from.html)
* [`from_list`]({{ site.url }}/documentation/operators/from.html)
* [`fromNodeCallback`]({{ site.url }}/documentation/operators/from.html)
* [`fromPromise`]({{ site.url }}/documentation/operators/from.html)
* [`fromRunnable`]({{ site.url }}/documentation/operators/from.html)
* [`Generate`]({{ site.url }}/documentation/operators/create.html)
* [`generateWithAbsoluteTime`]({{ site.url }}/documentation/operators/create.html)
* [`generateWithRelativeTime`]({{ site.url }}/documentation/operators/create.html)
* [`generator`]({{ site.url }}/documentation/operators/create.html)
* [`GetEnumerator`]({{ site.url }}/documentation/operators/to.html)
* [`getIterator`]({{ site.url }}/documentation/operators/to.html)
* [**`GroupBy`**]({{ site.url }}/documentation/operators/groupby.html)
* [`GroupByUntil`]({{ site.url }}/documentation/operators/groupby.html)
* [`GroupJoin`]({{ site.url }}/documentation/operators/join.html)
* [`head`]({{ site.url }}/documentation/operators/first.html)
* [`headOption`]({{ site.url }}/documentation/operators/first.html)
* [`headOrElse`]({{ site.url }}/documentation/operators/first.html)
* [`if`]({{ site.url }}/documentation/operators/defer.html)
* [`ifThen`]({{ site.url }}/documentation/operators/defer.html)
* [**`IgnoreElements`**]({{ site.url }}/documentation/operators/ignoreelements.html)
* [`indexOf`]({{ site.url }}/documentation/operators/contains.html)
* [`interleave`]({{ site.url }}/documentation/operators/merge.html)
* [`interpose`]({{ site.url }}/documentation/operators/to.html)
* [**`Interval`**]({{ site.url }}/documentation/operators/interval.html)
* [`into`]({{ site.url }}/documentation/operators/reduce.html)
* [`isEmpty`]({{ site.url }}/documentation/operators/contains.html)
* [`items`]({{ site.url }}/documentation/operators/just.html)
* [**`Join`**]({{ site.url }}/documentation/operators/join.html)
* [`join`]({{ site.url }}/documentation/operators/sum.html) (string)
* [`jortSort`]({{ site.url }}/documentation/operators/all.html)
* [`jortSortUntil`]({{ site.url }}/documentation/operators/all.html)
* [**`Just`**]({{ site.url }}/documentation/operators/just.html)
* [`keep`]({{ site.url }}/documentation/operators/map.html)
* [`keep-indexed`]({{ site.url }}/documentation/operators/map.html)
* [**`Last`**]({{ site.url }}/documentation/operators/last.html)
* [`lastOption`]({{ site.url }}/documentation/operators/last.html)
* [`LastOrDefault`]({{ site.url }}/documentation/operators/last.html)
* [`lastOrElse`]({{ site.url }}/documentation/operators/last.html)
* [`Latest`]({{ site.url }}/documentation/operators/first.html)
* [`latest`]({{ site.url }}/documentation/operators/switch.html) (Rx.rb version of **`Switch`**)
* [`length`]({{ site.url }}/documentation/operators/count.html)
* [`let`]({{ site.url }}/documentation/operators/publish.html)
* [`letBind`]({{ site.url }}/documentation/operators/publish.html)
* [`limit`]({{ site.url }}/documentation/operators/take.html)
* [`LongCount`]({{ site.url }}/documentation/operators/count.html)
* [`ManySelect`]({{ site.url }}/documentation/operators/flatmap.html)
* [**`Map`**]({{ site.url }}/documentation/operators/map.html)
* [`map`]({{ site.url }}/documentation/operators/zip.html) (RxClojure version of **`Zip`**)
* [`MapCat`]({{ site.url }}/documentation/operators/flatmap.html)
* [`mapCat`]({{ site.url }}/documentation/operators/zip.html) (RxClojure version of **`Zip`**)
* [`map-indexed`]({{ site.url }}/documentation/operators/map.html)
* [`mapTo`]({{ site.url }}/documentation/operators/map.html)
* [`mapWithIndex`]({{ site.url }}/documentation/operators/map.html)
* [**`Materialize`**]({{ site.url }}/documentation/operators/materialize-dematerialize.html)
* [**`Max`**]({{ site.url }}/documentation/operators/max.html)
* [`MaxBy`]({{ site.url }}/documentation/operators/max.html)
* [**`Merge`**]({{ site.url }}/documentation/operators/merge.html)
* [`mergeAll`]({{ site.url }}/documentation/operators/merge.html)
* [`merge_concurrent`]({{ site.url }}/documentation/operators/merge.html)
* [`mergeDelayError`]({{ site.url }}/documentation/operators/merge.html)
* [`mergeObservable`]({{ site.url }}/documentation/operators/merge.html)
* [`mergeWith`]({{ site.url }}/documentation/operators/merge.html)
* [**`Min`**]({{ site.url }}/documentation/operators/min.html)
* [`MinBy`]({{ site.url }}/documentation/operators/min.html)
* [`MostRecent`]({{ site.url }}/documentation/operators/first.html)
* [`Multicast`]({{ site.url }}/documentation/operators/publish.html)
* [`multicastWithSelector`]({{ site.url }}/documentation/operators/publish.html)
* [`nest`]({{ site.url }}/documentation/operators/to.html)
* [**`Never`**]({{ site.url }}/documentation/operators/empty-never-throw.html)
* [`Next`]({{ site.url }}/documentation/operators/takelast.html)
* [`Next`]({{ site.url }}/documentation/operators/first.html) (BlockingObservable version)
* [`none`]({{ site.url }}/documentation/operators/contains.html)
* [`nonEmpty`]({{ site.url }}/documentation/operators/contains.html)
* [`nth`]({{ site.url }}/documentation/operators/elementat.html)
* [**`ObserveOn`**]({{ site.url }}/documentation/operators/observeon.html)
* [`ObserveOnDispatcher`]({{ site.url }}/documentation/operators/observeon.html)
* [`observeSingleOn`]({{ site.url }}/documentation/operators/observeon.html)
* [`of`]({{ site.url }}/documentation/operators/from.html)
* [`of_array`]({{ site.url }}/documentation/operators/from.html)
* [`ofArrayChanges`]({{ site.url }}/documentation/operators/from.html)
* [`of_enumerable`]({{ site.url }}/documentation/operators/from.html)
* [`of_enumerator`]({{ site.url }}/documentation/operators/from.html)
* [`ofObjectChanges`]({{ site.url }}/documentation/operators/from.html)
* [`OfType`]({{ site.url }}/documentation/operators/filter.html)
* [`ofWithScheduler`]({{ site.url }}/documentation/operators/from.html)
* [`onBackpressureBlock`]({{ site.url }}/documentation/operators/backpressure.html)
* [`onBackpressureBuffer`]({{ site.url }}/documentation/operators/backpressure.html)
* [`onBackpressureDrop`]({{ site.url }}/documentation/operators/backpressure.html)
* [`OnErrorResumeNext`]({{ site.url }}/documentation/operators/catch.html)
* [`onErrorReturn`]({{ site.url }}/documentation/operators/catch.html)
* [`onExceptionResumeNext`]({{ site.url }}/documentation/operators/catch.html)
* [`orElse`]({{ site.url }}/documentation/operators/defaultifempty.html)
* [`pairs`]({{ site.url }}/documentation/operators/from.html)
* [`pairwise`]({{ site.url }}/documentation/operators/buffer.html)
* [`partition`]({{ site.url }}/documentation/operators/groupby.html)
* [`partition-all`]({{ site.url }}/documentation/operators/window.html)
* [`pausable`]({{ site.url }}/documentation/operators/backpressure.html)
* [`pausableBuffered`]({{ site.url }}/documentation/operators/backpressure.html)
* [`pluck`]({{ site.url }}/documentation/operators/map.html)
* [`product`]({{ site.url }}/documentation/operators/sum.html)
* [**`Publish`**]({{ site.url }}/documentation/operators/publish.html)
* [`PublishLast`]({{ site.url }}/documentation/operators/publish.html)
* [`publish_synchronized`]({{ site.url }}/documentation/operators/replay.html)
* [`publishValue`]({{ site.url }}/documentation/operators/publish.html)
* [`raise_error`]({{ site.url }}/documentation/operators/empty-never-throw.html)
* [**`Range`**]({{ site.url }}/documentation/operators/range.html)
* [**`Reduce`**]({{ site.url }}/documentation/operators/reduce.html)
* [`reductions`]({{ site.url }}/documentation/operators/scan.html)
* [**`RefCount`**]({{ site.url }}/documentation/operators/refcount.html)
* [**`Repeat`**]({{ site.url }}/documentation/operators/repeat.html)
* [`repeat_infinitely`]({{ site.url }}/documentation/operators/repeat.html)
* [`repeatWhen`]({{ site.url }}/documentation/operators/repeat.html)
* [**`Replay`**]({{ site.url }}/documentation/operators/replay.html)
* [`rescue_error`]({{ site.url }}/documentation/operators/catch.html)
* [`rest`]({{ site.url }}/documentation/operators/first.html)
* [**`Retry`**]({{ site.url }}/documentation/operators/retry.html)
* [`retry_infinitely`]({{ site.url }}/documentation/operators/retry.html)
* [`retryWhen`]({{ site.url }}/documentation/operators/retry.html)
* [`Return`]({{ site.url }}/documentation/operators/just.html)
* [`returnElement`]({{ site.url }}/documentation/operators/just.html)
* [`returnValue`]({{ site.url }}/documentation/operators/just.html)
* [`runAsync`]({{ site.url }}/documentation/operators/from.html)
* [**`Sample`**]({{ site.url }}/documentation/operators/sample.html)
* [**`Scan`**]({{ site.url }}/documentation/operators/scan.html)
* [`scope`]({{ site.url }}/documentation/operators/using.html)
* [`Select`]({{ site.url }}/documentation/operators/map.html) (alternate name of **`Map`**)
* [`select`]({{ site.url }}/documentation/operators/filter.html) (alternate name of **`Filter`**)
* [`selectConcat`]({{ site.url }}/documentation/operators/flatmap.html)
* [`selectConcatObserver`]({{ site.url }}/documentation/operators/flatmap.html)
* [`SelectMany`]({{ site.url }}/documentation/operators/flatmap.html)
* [`selectManyObserver`]({{ site.url }}/documentation/operators/flatmap.html)
* [`select_switch`]({{ site.url }}/documentation/operators/switch.html)
* [`selectSwitch`]({{ site.url }}/documentation/operators/flatmap.html)
* [`selectSwitchFirst`]({{ site.url }}/documentation/operators/flatmap.html)
* [`selectWithMaxConcurrent`]({{ site.url }}/documentation/operators/flatmap.html)
* [`select_with_index`]({{ site.url }}/documentation/operators/filter.html)
* [`seq`]({{ site.url }}/documentation/operators/from.html)
* [**`SequenceEqual`**]({{ site.url }}/documentation/operators/sequenceequal.html)
* [`sequence_eql?`]({{ site.url }}/documentation/operators/sequenceequal.html)
* [`SequenceEqualWith`]({{ site.url }}/documentation/operators/sequenceequal.html)
* [**`Serialize`**]({{ site.url }}/documentation/operators/serialize.html)
* [`share`]({{ site.url }}/documentation/operators/refcount.html)
* [`shareReplay`]({{ site.url }}/documentation/operators/replay.html)
* [`shareValue`]({{ site.url }}/documentation/operators/refcount.html)
* [`Single`]({{ site.url }}/documentation/operators/first.html)
* [`SingleOrDefault`]({{ site.url }}/documentation/operators/first.html)
* [`singleOption`]({{ site.url }}/documentation/operators/first.html)
* [`singleOrElse`]({{ site.url }}/documentation/operators/first.html)
* [`size`]({{ site.url }}/documentation/operators/count.html)
* [**`Skip`**]({{ site.url }}/documentation/operators/skip.html)
* [**`SkipLast`**]({{ site.url }}/documentation/operators/skiplast.html)
* [`skipLastWithTime`]({{ site.url }}/documentation/operators/skiplast.html)
* [**`SkipUntil`**]({{ site.url }}/documentation/operators/skipuntil.html)
* [`skipUntilWithTime`]({{ site.url }}/documentation/operators/skipuntil.html)
* [**`SkipWhile`**]({{ site.url }}/documentation/operators/skipwhile.html)
* [`skipWhileWithIndex`]({{ site.url }}/documentation/operators/skipwhile.html)
* [`skip_with_time`]({{ site.url }}/documentation/operators/skip.html)
* [`slice`]({{ site.url }}/documentation/operators/filter.html)
* [`sliding`]({{ site.url }}/documentation/operators/window.html)
* [`slidingBuffer`]({{ site.url }}/documentation/operators/buffer.html)
* [`some`]({{ site.url }}/documentation/operators/contains.html)
* [`sort`]({{ site.url }}/documentation/operators/to.html)
* [`sort-by`]({{ site.url }}/documentation/operators/to.html)
* [`sorted-list-by`]({{ site.url }}/documentation/operators/to.html)
* [`split`]({{ site.url }}/documentation/operators/flatmap.html)
* [`split-with`]({{ site.url }}/documentation/operators/groupby.html)
* [**`Start`**]({{ site.url }}/documentation/operators/start.html)
* [`startAsync`]({{ site.url }}/documentation/operators/start.html)
* [`startFuture`]({{ site.url }}/documentation/operators/start.html)
* [**`StartWith`**]({{ site.url }}/documentation/operators/startwith.html)
* [`startWithArray`]({{ site.url }}/documentation/operators/startwith.html)
* [`stringConcat`]({{ site.url }}/documentation/operators/sum.html)
* [`stopAndWait`]({{ site.url }}/documentation/operators/backpressure.html)
* [`subscribe`]({{ site.url }}/documentation/operators/subscribe.html)
* [**`SubscribeOn`**]({{ site.url }}/documentation/operators/subscribeon.html)
* [`SubscribeOnDispatcher`]({{ site.url }}/documentation/operators/subscribeon.html)
* [`subscribeOnCompleted`]({{ site.url }}/documentation/operators/subscribe.html)
* [`subscribeOnError`]({{ site.url }}/documentation/operators/subscribe.html)
* [`subscribeOnNext`]({{ site.url }}/documentation/operators/subscribe.html)
* [**`Sum`**]({{ site.url }}/documentation/operators/sum.html)
* [`sumDouble`]({{ site.url }}/documentation/operators/sum.html)
* [`sumFloat`]({{ site.url }}/documentation/operators/sum.html)
* [`sumInteger`]({{ site.url }}/documentation/operators/sum.html)
* [`sumLong`]({{ site.url }}/documentation/operators/sum.html)
* [**`Switch`**]({{ site.url }}/documentation/operators/switch.html)
* [`switchCase`]({{ site.url }}/documentation/operators/defer.html)
* [`switchIfEmpty`]({{ site.url }}/documentation/operators/defaultifempty.html)
* [`switchLatest`]({{ site.url }}/documentation/operators/switch.html)
* [`switchMap`]({{ site.url }}/documentation/operators/flatmap.html)
* [`switchOnNext`]({{ site.url }}/documentation/operators/switch.html)
* [`Synchronize`]({{ site.url }}/documentation/operators/serialize.html)
* [**`Take`**]({{ site.url }}/documentation/operators/take.html)
* [`take_with_time`]({{ site.url }}/documentation/operators/take.html)
* [`takeFirst`]({{ site.url }}/documentation/operators/first.html)
* [**`TakeLast`**]({{ site.url }}/documentation/operators/takelast.html)
* [`takeLastBuffer`]({{ site.url }}/documentation/operators/takelast.html)
* [`takeLastBufferWithTime`]({{ site.url }}/documentation/operators/takelast.html)
* [`takeLastWithTime`]({{ site.url }}/documentation/operators/takelast.html)
* [`takeRight`]({{ site.url }}/documentation/operators/last.html) (see also: [**`TakeLast`**]({{ site.url }}/documentation/operators/takelast.html))
* [**`TakeUntil`**]({{ site.url }}/documentation/operators/takeuntil.html)
* [`takeUntilWithTime`]({{ site.url }}/documentation/operators/takeuntil.html)
* [**`TakeWhile`**]({{ site.url }}/documentation/operators/takewhile.html)
* [`takeWhileWithIndex`]({{ site.url }}/documentation/operators/takewhile.html)
* [`tail`]({{ site.url }}/documentation/operators/takelast.html)
* [`tap`]({{ site.url }}/documentation/operators/do.html)
* [`tapOnCompleted`]({{ site.url }}/documentation/operators/do.html)
* [`tapOnError`]({{ site.url }}/documentation/operators/do.html)
* [`tapOnNext`]({{ site.url }}/documentation/operators/do.html)
* [**`Then`**]({{ site.url }}/documentation/operators/and-then-when.html)
* [`thenDo`]({{ site.url }}/documentation/operators/and-then-when.html)
* [`Throttle`]({{ site.url }}/documentation/operators/debounce.html)
* [`throttleFirst`]({{ site.url }}/documentation/operators/sample.html)
* [`throttleLast`]({{ site.url }}/documentation/operators/sample.html)
* [`throttleWithSelector`]({{ site.url }}/documentation/operators/debounce.html)
* [`throttleWithTimeout`]({{ site.url }}/documentation/operators/debounce.html)
* [**`Throw`**]({{ site.url }}/documentation/operators/empty-never-throw.html)
* [`throwError`]({{ site.url }}/documentation/operators/empty-never-throw.html)
* [`throwException`]({{ site.url }}/documentation/operators/empty-never-throw.html)
* [**`TimeInterval`**]({{ site.url }}/documentation/operators/timeinterval.html)
* [**`Timeout`**]({{ site.url }}/documentation/operators/timeout.html)
* [`timeoutWithSelector`]({{ site.url }}/documentation/operators/timeout.html)
* [**`Timer`**]({{ site.url }}/documentation/operators/timer.html)
* [**`Timestamp`**]({{ site.url }}/documentation/operators/timestamp.html)
* [**`To`**]({{ site.url }}/documentation/operators/to.html)
* [`to_a`]({{ site.url }}/documentation/operators/to.html)
* [`ToArray`]({{ site.url }}/documentation/operators/to.html)
* [`ToAsync`]({{ site.url }}/documentation/operators/start.html)
* [`toBlocking`]({{ site.url }}/documentation/operators/to.html)
* [`toBuffer`]({{ site.url }}/documentation/operators/to.html)
* [`to_dict`]({{ site.url }}/documentation/operators/to.html)
* [`ToDictionary`]({{ site.url }}/documentation/operators/to.html)
* [`ToEnumerable`]({{ site.url }}/documentation/operators/to.html)
* [`ToEvent`]({{ site.url }}/documentation/operators/to.html)
* [`ToEventPattern`]({{ site.url }}/documentation/operators/to.html)
* [`ToFuture`]({{ site.url }}/documentation/operators/to.html)
* [`to_h`]({{ site.url }}/documentation/operators/to.html)
* [`toIndexedSeq`]({{ site.url }}/documentation/operators/to.html)
* [`toIterable`]({{ site.url }}/documentation/operators/to.html)
* [`toIterator`]({{ site.url }}/documentation/operators/to.html)
* [`ToList`]({{ site.url }}/documentation/operators/to.html)
* [`ToLookup`]({{ site.url }}/documentation/operators/to.html)
* [`toMap`]({{ site.url }}/documentation/operators/to.html)
* [`toMultiMap`]({{ site.url }}/documentation/operators/to.html)
* [`ToObservable`]({{ site.url }}/documentation/operators/from.html)
* [`toSet`]({{ site.url }}/documentation/operators/to.html)
* [`toSortedList`]({{ site.url }}/documentation/operators/to.html)
* [`toStream`]({{ site.url }}/documentation/operators/to.html)
* [`ToTask`]({{ site.url }}/documentation/operators/to.html)
* [`toTraversable`]({{ site.url }}/documentation/operators/to.html)
* [`toVector`]({{ site.url }}/documentation/operators/to.html)
* [`tumbling`]({{ site.url }}/documentation/operators/window.html)
* [`tumblingBuffer`]({{ site.url }}/documentation/operators/buffer.html)
* [`unsubscribeOn`]({{ site.url }}/documentation/operators/subscribeon.html)
* [**`Using`**]({{ site.url }}/documentation/operators/using.html)
* [**`When`**]({{ site.url }}/documentation/operators/and-then-when.html)
* [`Where`]({{ site.url }}/documentation/operators/filter.html)
* [`while`]({{ site.url }}/documentation/operators/repeat.html)
* [`whileDo`]({{ site.url }}/documentation/operators/repeat.html)
* [**`Window`**]({{ site.url }}/documentation/operators/window.html)
* [`windowWithCount`]({{ site.url }}/documentation/operators/window.html)
* [`windowWithTime`]({{ site.url }}/documentation/operators/window.html)
* [`windowWithTimeOrCount`]({{ site.url }}/documentation/operators/window.html)
* [`windowed`]({{ site.url }}/documentation/operators/backpressure.html)
* [`withFilter`]({{ site.url }}/documentation/operators/filter.html)
* [`withLatestFrom`]({{ site.url }}/documentation/operators/combinelatest.html)
* [**`Zip`**]({{ site.url }}/documentation/operators/zip.html)
* [`zipArray`]({{ site.url }}/documentation/operators/zip.html)
* [`zipWith`]({{ site.url }}/documentation/operators/zip.html)
* [`zipWithIndex`]({{ site.url }}/documentation/operators/zip.html)
* [`++`]({{ site.url }}/documentation/operators/concat.html)
* [`+:`]({{ site.url }}/documentation/operators/startwith.html)
* [`:+`]({{ site.url }}/documentation/operators/just.html)
