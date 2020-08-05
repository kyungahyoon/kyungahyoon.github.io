---
layout: post
title:  "네비게이션 가드"
date:   2020-07-24 11:39:58 +0900
categories: jekyll update
---

네비게이션 가드란 뷰 라우터로 특정 URL에 접근할 때 해당 URL의 접근을 막는 방법을 말한다. 
ex) 사용자의 인증 정보가 없으면 특정 페이지에 접근하지 못하게 할 때 사용하는 기술.

# 네비게이션 가드의 종류 

- 애플리케이션 전역에서 동작하는 전역 가드
- 특정 URL에서만 동작하는 라우터 가드 
- 라우터 컴포넌트 안에 정의하는 컴포넌트 가드 

# 전역 가드 
전역 가드는 라우터 인스턴스를 참조하는 객체로 설정할 수 있다. 

먼저, 전역 가드 설정을 위해 아래와 같이 라우터 인스턴스를 생성한다. 

{% highlight ruby %}

var router = new VueRouter();

{% endhighlight %}

다음으로 router 변수에 아래와 같이 .beforeEach() API를 호출한다.

{% highlight ruby %}
router.beforeEach(function (to, from, next) {
    //to : 이동할 url 
    //from : 현재 url
    // next : to에서 지정한 url로 이동하기 위해 꼭 호출해야 하는 함수
});
{% endhighlight %}

여기서 beforeEach()를 호출하면 다음과 같이 3개의 인자를 받는다.

- to : 이동할 url 정보가 담긴 라우터 객체 
- from : 현재 url 정보가 담긴 라우터 객체 
- next : to에서 지정한 url로 이동하기 위해 꼭 호출해야 하는 함수

router.beforeEach()를 호출하고 나면 모든 라우팅이 대기 상태가 된다. 여기서 해당 url로 라우팅 하기 위해서는 next()를 호출해줘야 한다.    
next()가 호출되기 전까지 화면이 전환되지 않는다.    

`전역 가드 동작 예제`
{% highlight ruby %}
// 라우터 컴포넌트
var Login = { template: '<p>Login Component</p>' };
var Home = { template: '<p>Home Component</p>' };

// 라우팅 정보
var router = new VueRouter({
  routes: [
    { path: '/login', component: Login },
    { path: '/home', component: Home }
  ]
});
{% endhighlight %}