---
layout: post
title:  "Vuex 스토어 속성 모듈화 방법2"
date:   2020-07-24 11:39:58 +0900
categories: jekyll update
---

앱이 비대해져서 1개의 store로는 관리가 힘들 때 modules 속성을 사용한다.

{% highlight ruby %}
//store.js

import Vue from from 'vue'
import Vuex from 'vuex'
import todo from 'modules/todo.js'

export const store = new Vuex.Store({
	modules: {
	moduleA: todo, //모듈 명칭 : 모듈 파일명
	todo // todo: todo
}

//todo.js
const state = {}
const getters = {}
const mutations = {}
const actions = {}
});
{% endhighlight %}
