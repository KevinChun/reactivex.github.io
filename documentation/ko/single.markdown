---
layout: documentation
title: ReactiveX - Single
id: single
---

<h1>Single</h1>
<p>
 RxJava(그리고 RxGroovy &amp; RxScala와 같은 RX의 파생 기술들)는 <a href="observable.html">Observable</a>과 유사한 &ldquo;Single.&rdquo;를 구현해서 제공한다.
</p>
<p>
 Single은 Obvservable의 한 형태이지만, Observable처럼 존재하지 않는 곳에서부터 무한대까지의 임이의 연속된 값들을 배출하는 것과는 달리, 항상 한 가지 값 또는 오류 알림 중 하나만을 배출한다.
</p>
<p>
 이런 이유 때문에, Single을 구독할 때는 Observable을 구독할 때 사용하는 세 개의 메서드(<tt>onNext</tt>, <tt>onError</tt>, and <tt>onCompleted</tt>) 대신 다음의 두 메서드만 사용할 수 있다:
</p>
<dl>
 <dt>onSuccess</dt>
  <dd>Single은 자신이 배출하는 하나의 값을 이 메서드를 통해 전달한다</dd>
 <dt>onError</dt>
  <dd>Single은 항목을 배출할 수 없을 때 이 메서드를 통해 Throwable 객체를 전달한다</dd>
</dl>
<p>
 Single은 이 메서드 중 하나만 그리고 한 번만 호출할 것이다. 메서드가 호출되면 Single 객체는 종료되고 구독 역시 끝난다.
</p>

<h1>Single 연산자를 통한 구성</h1>
<p>
 Observable과 마찬가지로, Single도 다양한 연산자들을 제공한다. 이 중 어떤 연산자들은 Observable과 Single을 섞어서 사용할 수 있도록 Observable의 영역과 Single의 영역을 이으는 인터페이스 역할을 한다:
</p>
<table>
 <thead>
  <tr><th>연산자</th><th>리턴 타입</th><th>설명</th></tr>
 </thead>
 <tbody>
  <tr><td><tt>compose</tt></td><td><tt>Single</tt></td><td>이 연산자를 사용해서 사용자 정의 연산자를 만들 수 있다</td></tr>
  <tr><td><tt>concat</tt> 그리고 <tt>concatWith</tt></td><td><tt>Observable</tt></td><td>여러 개의 Single이 배출한 항목들을 Observable이 배출하는 형태로 변환한다</td></tr>
  <tr><td><tt>create</tt></td><td><tt>Single</tt></td><td>명시적인 subscriber 메서드 호출을 통해 Single을 생성한다</td></tr>
  <tr><td><tt>delay</tt></td><td><tt>Single</tt></td><td>Single이 항목을 배출하는 시간을 전달된 시간 만큼 지연시킨다</td></tr>
  <tr><td><tt>doOnError</tt></td><td><tt>Single</tt></td><td>onError 메서드가 호출될 때 전달한 메서드를 실행하는 Single을 리턴한다</td></tr>
  <tr><td><tt>doOnSuccess</tt></td><td><tt>Single</tt></td><td>onSuccess 메서드가 호출될 때 전달한 메서드를 실행하는 Single을 리턴한다</td></tr>
  <tr><td><tt>error</tt></td><td><tt>Single</tt></td><td>오류를 구독하는 구독자에게 즉시 오류가 발생했음을 알리는 Single을 리턴한다</td></tr>
  <tr><td><tt>flatMap</tt></td><td><tt>Single</tt></td><td>Single이 배출하는 항목에 적용된 함수의 결과를 담은 Single을 리턴한다</td></tr>
  <tr><td><tt>flatMapObservable</tt></td><td><tt>Observable</tt></td><td>Single이 배출한 항목에 적용된 함수의 결과를 담은 Observable을 리턴한다</td></tr>
  <tr><td><tt>from</tt></td><td><tt>Single</tt></td><td>퓨처를 Single로 변환한다</td></tr>
  <tr><td><tt>just</tt></td><td><tt>Single</tt></td><td>명시한 항목을 배출하는 Single을 리턴한다</td></tr>
  <tr><td><tt>map</tt></td><td><tt>Single</tt></td><td>소스 Single이 배출한 항목에 적용된 함수의 결과를 배출하는 Single을 리턴한다</td></tr>
  <tr><td><tt>merge</tt></td><td><tt>Single</tt></td><td>두 번째 Single을 배출하는 Single을 전달 받은 후, 두 번째 Single이 배출한 항목을 배출한다</td></tr>
  <tr><td><tt>merge</tt> 그리고 <tt>mergeWith</tt></td><td><tt>Observable</tt></td><td>여러 Single이 배출한 항목들을 머지 후 Observable이 배출하는 형태로 리턴한다</td></tr>
  <tr><td><tt>observeOn</tt></td><td><tt>Single</tt></td><td>특정 <a href="scheduler.html">Scheduler</a> 상에서 구독자 메서드를 호출하는 Single을 리턴한다</td></tr>
  <tr><td><tt>onErrorReturn</tt></td><td><tt>Single</tt></td><td>명시된 항목을 배출하는 Single을 오류 알림을 보내는 Single로 변환한다</td></tr>
  <tr><td><tt>subscribeOn</tt></td><td><tt>Single</tt></td><td>특정 <a href="scheduler.html">Scheduler</a> 상에서 동작하는 Single을 리턴한다</td></tr>
  <tr><td><tt>timeout</tt></td><td><tt>Single</tt></td><td>returns a Single that makes an error notification if the source Single does not emit a value in a specified time period</td></tr>
  <tr><td><tt>toSingle</tt></td><td><tt>Single</tt></td><td>converts an Observable that emits a single item into a Single that emits that item</td></tr>
  <tr><td><tt>toObservable</tt></td><td><tt>Observable</tt></td><td>converts a Single into an Observable that emits the item emitted by the Single and then completes</td></tr>
  <tr><td><tt>zip</tt> and <tt>zipWith</tt></td><td><tt>Single</tt></td><td>returns a Single that emits an item that is the result of a function applied to items emitted by two or more other Singles</td></tr>
 </tbody>
</table>
<p>
 The following sections of this page will give marble diagrams that explain these operators schematically. This
 diagram explains how Singles are represented in marble diagrams:
</p>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.legend.png" width="100%" />
<h2>compose</h2>
<h2>concat and concatWith</h2>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.concat.png" width="100%" />
<p>
 There is also an instance version of this operator:
</p>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.concatWith.png" width="100%" />
<h2>create</h2>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.create.png" width="100%" />
<h2>delay</h2>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.delay.png" width="100%" />
<p>
 There is also a version of this operator that allows you to perform the delay on a particular
 <a href="scheduler.html">Scheduler</a>:
</p>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.delay.s.png" width="100%" />
<h2>doOnError</h2>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.doOnError.png" width="100%" />
<h2>doOnSuccess</h2>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.doOnSuccess.png" width="100%" />
<h2>error</h2>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.error.png" width="100%" />
<h2>flatMap</h2>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.flatMap.png" width="100%" />
<h2>flatMapObservable</h2>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.flatMapObservable.png" width="100%" />
<h2>from</h2>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.from.Future.png" width="100%" />
<p>There is also a variety that takes a <a href="scheduler.html">Scheduler</a> as an argument:
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.from.Future.s.png" width="100%" />
<h2>just</h2>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.just.png" width="100%" />
<h2>map</h2>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.map.png" width="100%" />
<h2>merge and mergeWith</h2>
<p>
 One version of merge takes a Single that emits a second Single and converts it into a Single that emits the
 item emitted by that second Single:
</p>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.merge.oo.png" width="100%" />
<p>
 Another version takes two or more Singles and merges them into an Observable that emits the items emitted by
 the source Singles (in an arbitrary order):
</p>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.merge.png" width="100%" />
<h2>observeOn</h2>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.observeOn.png" width="100%" />
<h2>onErrorReturn</h2>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.onErrorReturn.png" width="100%" />
<h2>subscribeOn</h2>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.subscribeOn.png" width="100%" />
<h2>timeout</h2>
<p>
 Timeout will cause a Single to abort with an error notification if it does not emit an item in a specified
 period of time after it is subscribed to. One version allows you to set this time out by means of a number of
 specified time units:
</p>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.timeout.1.png" width="100%" />
<p>
 You can also specify a particular <a href="scheduler.html">Scheduler</a> for the timer to operate on:
</p>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.timeout.1s.png" width="100%" />
<p>
 A version of the timeout operator allows you to switch to a backup Single rather than sending an error
 notification if the timeout expires:
</p>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.timeout.2.png" width="100%" />
<p>
 This, too, has a <a href="scheduler.html">Scheduler</a>-specific version:
</p>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.timeout.2s.png" width="100%" />
<h2>toObservable</h2>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.toObservable.png" width="100%" />
<h2>zip and zipWith</h2>
<img src="https://raw.github.com/wiki/ReactiveX/RxJava/images/rx-operators/Single.zip.png" width="100%" />
