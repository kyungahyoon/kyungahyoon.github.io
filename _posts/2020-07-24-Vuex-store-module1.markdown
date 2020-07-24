---
layout: post
title:  "Vuex 스토어 속성 모듈화 방법1"
date:   2020-07-24 11:39:58 +0900
categories: jekyll update
---

method가 길어지면 어떤 state를 바라보는지 확인하기 어렵기 때문에 모듈화가 필요하다.

{% highlight ruby %}
//store.js
import Vue from 'vue'
import Vuex from 'vuex'

export const store = new Vuex.Store({
	state: {},
	getters: {},
	mutations: {},
	actions: {}
})
{% endhighlight %}

위의 속성들을 ES6의 Import&Export를 이용하여 아래와 같이 속성별로 모듈화 할 수 있다. 

{% highlight ruby %}
import Vue from 'vue'
import Vuex from 'vuex'
import * as getters from './getters'
import * as mutations from './mutations'

export const store = new Vuex.Store({
	getters,
	mutations
})
{% endhighlight %}
