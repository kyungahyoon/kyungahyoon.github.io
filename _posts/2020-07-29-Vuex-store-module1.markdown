---
layout: post
title:  "Vuex와 State"
---

`Vuex란?`
컴포넌트 간의 통신이나 데이터 전달을 좀 더 유기적으로 관리하기 위한 패턴이자 라이브러리.
다른 상태 관리 패턴이나 라이브러리를 비교했을 때 뷰의 Reactivity 체계를 효율적으로 활용하여 화면을 업데이트 한다는 차이점이 있다.

{% highlight ruby %}
new Vue({
  // state
  data () {
    return {
      count: 0
    }
  },
  // view
  template: `
    <div>{{ count }}</div>
  `,
  // actions
  methods: {
    increment () {
      this.count++
    }
  }
})
{% endhighlight %}

`상태 관리로 해결할 수 있는 문제점`
1. 뷰의 컴포넌트 통신 방식인 props, event emit 때문에 중간에 거쳐야 할 컴포넌트가 많아지거나 
2. 이를 피하기 위해 Event Bus를 사용하여 컴포넌트 간 데이터 흐름을 파악하기 어려운 것을 해결할 수 있다.

`Vuex 컨셉`
- State : 컴포넌트 간에 공유하는 데이터 data()
- View : 데이터를 표시하는 화면 template
- Action : 사용자의 입력에 따라 데이터를 변경하는 methods

`Vuex 구조`
뷰 컴포넌트 > 비동기 로직 > 동기 로직 > 상태 
- 시작점은 Vue Components 
- 컴포넌트에서 비동기 로직(Method를 선언해서 API를 콜하는 부분)인 Actions를 콜하고,
- Actions는 비동기 로직만 처리할 뿐 State(Data)를 직접 변경하진 않음.
- Actions가 동기 로직인 Mutations를 호출해서 State(Data)를 변경한다.
- Mutations 에서만 State(Data)를 변경할 수 있다. 


