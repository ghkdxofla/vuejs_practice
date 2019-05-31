# Vue.js Practice

0. Vue.js란?

- Front-end UI용 프레임워크
- 점진적으로 채택이 가능한 것이 특징
- View Layer에 초점을 맞추어 라이브러리, 기존 프로젝트와 통합이 용이함

1. 선언적 렌더링

- v-bind : 디렉티브
    * v- 접두어의 경우 Vue에서 제공하는 특수 속성이며, 렌더링된 DOM에 특수한 반응형 동작 수행


2. 진입, 진출, 리스트 트랜지션

- transition 컴포넌트로 싸여진 엘리먼트가 삽입되거나 제거 될 때 발생
- 트랜지션 클래스
    * v-enter: enter의 시작 상태. 엘리먼트가 삽입되기 전에 적용되고 한 프레임 후에 제거됩니다.
    * v-enter-active: enter에 대한 활성 및 종료 상태. 엘리먼트가 삽입되기 전에 적용됩니다. 트랜지션 / 애니메이션이 완료되면 제거됩니다.
    * v-enter-to: 2.1.8 이상 버전에서 지원합니다. 진입 상태의 끝에서 실행됩니다. 엘리먼트가 삽입된 후 (동시에 v-enter가 제거됨), 트랜지션/애니메이션이 끝나면 제거되는 하나의 프레임을 추가했습니다.
    * v-leave: leave를 위한 시작 상태. 진출 트랜지션이 트리거 될 때 적용되고 한 프레임 후에 제거됩니다.
    * v-leave-active: leave에 대한 활성 및 종료 상태. 진출 트랜지션이 트리거되면 적용되고 트랜지션 / 애니메이션이 완료되면 제거됩니다.
    * v-leave-to: 2.1.8 이상 버전에서 지원합니다. 진출 상태의 끝에서 실행됩니다. 진출 트랜지션이 트리거되고 (동시에 v-leave가 제거됨), 트랜지션/애니메이션이 끝나면 제거되는 하나의 프레임을 추가했습니다.
    * ex : <transition name = "my-transition">을 사용하면v-enter 클래스는 my-transition-enter 가 됩니다.
- JS 훅: enter, leave 훅에서 done 콜백 필요
    * 이렇게 안하면 동기적으로 호출되고 트랜지션은 즉시 완료됨
    * ex :
```
<!-- html -->
<transition
  v-on:before-enter="beforeEnter"
  v-on:enter="enter"
  v-on:after-enter="afterEnter"
  v-on:enter-cancelled="enterCancelled"

  v-on:before-leave="beforeLeave"
  v-on:leave="leave"
  v-on:after-leave="afterLeave"
  v-on:leave-cancelled="leaveCancelled"
>
  <!-- ... -->
</transition>
```
```
<!-- javaScript -->
methods: {
  // --------
  // 진입
  // --------

  beforeEnter: function (el) {
    // ...
  },
  // done 콜백은 CSS와 함께 사용할 때 선택 사항입니다.
  enter: function (el, done) {
    // ...
    done()
  },
  afterEnter: function (el) {
    // ...
  },
  enterCancelled: function (el) {
    // ...
  },

  // --------
  // 진출
  // --------

  beforeLeave: function (el) {
    // ...
  },
  // done 콜백은 CSS와 함께 사용할 때 선택 사항입니다.
  leave: function (el, done) {
    // ...
    done()
  },
  afterLeave: function (el) {
    // ...
  },
  // leaveCancelled은 v-show와 함께 사용됩니다.
  leaveCancelled: function (el) {
    // ...
  }
}methods: {
  // --------
  // 진입
  // --------

  beforeEnter: function (el) {
    // ...
  },
  // done 콜백은 CSS와 함께 사용할 때 선택 사항입니다.
  enter: function (el, done) {
    // ...
    done()
  },
  afterEnter: function (el) {
    // ...
  },
  enterCancelled: function (el) {
    // ...
  },

  // --------
  // 진출
  // --------

  beforeLeave: function (el) {
    // ...
  },
  // done 콜백은 CSS와 함께 사용할 때 선택 사항입니다.
  leave: function (el, done) {
    // ...
    done()
  },
  afterLeave: function (el) {
    // ...
  },
  // leaveCancelled은 v-show와 함께 사용됩니다.
  leaveCancelled: function (el) {
    // ...
  }
}
```

# JavaScript 참고

- _ 의 의미 : 
    * 참고 : http://webframeworks.kr/tutorials/translate/explanation-of-this-in-javascript-1/