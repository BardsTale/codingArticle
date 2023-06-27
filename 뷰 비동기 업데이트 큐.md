### 뷰의 비동기 업데이트 큐(Async update queue)에 대해서 원본 가이드를 번역 및 개인 의견을 가미하여 작성한 글 입니다.
#### 원본 링크 : https://dev.to/codeoz/vue-academy-6-async-update-queue-56k
<br>

## 뷰 비동기 업데이트 큐(Async update queue)

Vue는 비동기적으로 DOM 업데이트를 수행합니다.<br>
이 말이 의미하는 바를 비동기 업데이트 큐를 사용하지 않은 아래의 일반적인 케이스를 통해 설명하겠습니다.<br>
<br>
### 일반적인 케이스
My Array란 DOM Element를 담을 특정한 배열이 있고 이 배열에 새로운 Element를 push 할 때마다 DOM을 렌더링을 한다고 가정합니다.  

![image](https://user-images.githubusercontent.com/62861679/193981752-c10e7628-5340-4ffc-95d2-c942c3aa64af.png)
<br>
몇 개의 element만 추가한다면 그다지 큰 문제점을 느낄 수 없겠지만 만약 배열에 1000개의 DOM Element를 순차적으로 push할 경우,<br>
DOM을 1000회 렌더링 할 것이라고 상상해보시죠! DOM은 <b>BOOM!</b> 폭팔할 것입니다..🤯<br>
<br>
사실 이런 경우 DOM을 1000회 업데이트 할 필요는 없고 요청된 1000개의 DOM Element를 한 번만 DOM을 업데이트 하는 것이 맞습니다.<br>
<br>
### 비동기 업데이트 큐

Vue는 비동기 업데이트 큐를 통해 비동기적으로 DOM 업데이트를 수행합니다.<br>
바인딩 된 데이터의 변경이 관찰 될 때마다(위의 경우 My Array에 항목 추가) DOM을 즉시 업데이트 하지 않고<br>
<b>모든 변경 사항을 대기열(큐, 버퍼)에 추가합니다.</b><br>
<br>
그리고 일정 시간(위의 경우 My Array에 모든 DOM Element를 추가하는 데 필요한 시간)을 기다린 후 DOM을 업데이트 합니다.<br>
이러한 작동 원리에 따라 1000개의 DOM Element를 추가하지만 DOM은 <b>오직 한 번만 업데이트 하는 것입니다.</b><br>
<br>
![image](https://user-images.githubusercontent.com/62861679/194177853-2eff196c-0873-46d2-8f7c-e26302c8467b.png)<br>
<br>
이러한 대기열을 사용한 중복 행위 제거는 불필요한 계산과 DOM 조작을 방지하는 데 중요한 역할은 합니다.<br>
그리고 이제 Vue에서 우리는 큐가 DOM을 업데이트 하는 순간을 <code>tick</code>이라고 부를 것입니다!<br>
<br>
일반적으로 DOM 상태에 따라 개발을 하는 경우를 제외하곤 이러한 작동원리에 대해 주의할 필요가 없습니다.<br>
다만 Vue에선 DOM 상태에 따라 개발을 하는 것은 권장되지 않으며(getElementById 등의)<br>
DOM 상태 대신 구성 요소의 상태를 사용하는 것이 좋습니다.<br>
<br>
### tick 원리에 대한 예제 코드
```vue
<div id="example">{{ message }}</div>  
```
```javascript
const vm = new Vue({
  el: '#example',
  data: {
    message: '123'
  }
})

vm.message = 'new message' // 데이터를 변경하지만, Vue가 즉시 리렌더링을 수행하지 않습니다!

vm.$el.textContent === 'new message' // 변경 내역이 아직 큐에 있고 DOM에서 현재 업데이트 되지 않았기 때문에 false

// NextTick은 큐의 변경 내역이 모두 업데이트가 되었다는 것을 보장합니다!
Vue.nextTick(function () {
  // DOM이 마침내 변경이 완료되었습니다!
  vm.$el.textContent === 'new message' // true
})
```


위의 코드는 Vue에서 Dom이 변경되는 시점에 관한 예제 코드이며 nextTick 콜백 함수를 사용하여 이를 설명하고 있습니다.<br>
<b>*참고로 vue 3.0 공식 가이드에서는 this.$nextTick() 방식으로 사용하는 것을 안내하고 있으며,<br>
또한 Promise를 반환하므로 async/await 문법 활용이 가능합니다.</b><br>
<br>
우리는 종종 예제 코드와 같이 기대값이 DOM에서 업데이트 되었는지 확인 후 다음 로직을 진행할 때가 있습니다.<br>
이 경우 DOM 업데이트를 보장하는 <code>nextTick</code>을 사용하면 되며 vue 트랜지션 코드를 사용하는 경우 <b>[트랜지션훅](https://v3.ko.vuejs.org/guide/transitions-enterleave.html#javascript-%E1%84%92%E1%85%AE%E1%86%A8)</b>을 통해서도 가능합니다.

<br>
<br>

### 결론
Vue는 비동이 업데이트 큐를 사용하므로 <code>tick</code> 이후에만 DOM을 업데이트 하며<br>
이는 DOM에 불필요한 업데이트를 방지할 수 있으므로 훨씬 효율적이며 저렴합니다.<br>
또한 <code>tick</code>이 일어난 이후 렌더링을 하는 시점에서 가상 DOM을 통해 리렌더링 및 계산을 수행하므로 일반적인 real DOM을 다루는 방식 보다<br>
효율적이게 작동하게 되는 것입니다! <b>wow~!</b><br>
<br>
![밀하우스](https://media1.giphy.com/media/bYpgM8bi7QV3i/giphy.gif?cid=ecf05e475420fcaogdbqs22j3qf5ubqg9moywbvz7cf7mhul&rid=giphy.gif&ct=g)
