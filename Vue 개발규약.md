## Vue 개발 규약
<br>
Vue 3.0 스타일 가이드 공식 문서와 기타 Vue 공식 문서를 기반으로 작성된 Vue 개발 규약입니다.<br>
스타일 가이드의 우선순위 규칙 4단계(A:필수, B:강력추천, C:추천, D:주의해서 사용)에서 A~C 중에서 선별한 것과<br>
개인적으로 필요하다고 생각한 내용들을 추가한 개발 규약임을 알려드립니다.<br>
<br><br>



### 1. SFC(싱글 파일 컴포넌트) 파일 명명 규칙

SFC 파일 명명 규칙은  여섯 가지입니다.
<br><br>

![image](https://github.com/BardsTale/vue_guide/assets/62861679/cc402846-d602-460b-b216-de30bd0c4332)

> **첫 번째**, 컴포넌트 이름은 Root 컴포넌트인 App과 Vue에서 제공하는 내장 컴포넌트(**<transition>**, **<component>** 등)를 제외하곤<br>항상 두 단어 이상의 합성어를 사용합니다.<br>
모든 HTML 엘리먼트의 이름은 한 단어이기 때문에 합성어를 사용하는 것은 기존 그리고 향후 HTML 엘리먼트와의 충돌을 방지하고 Vue 컴포넌트를 명확히 구분할 수 있습니다.<br>
<br>

> **두 번째**, 컴포넌트 이름은 항상  항상 파스칼 케이스(PascalCase)여야 합니다.<br>
위의 첫 번째 합성어에 의거하여 두 단어를 사용할 수 있는 네이밍 컨벤션 중에서 고려할 수 있는건 파스칼 케이스와 케밥 케이스입니다.<br>
주 사용하는 개발 환경 OS인 윈도우와 맥OS는 파일시스템의 대소문자 구분에 문제가 없으므로 가장 최적화가 좋은 파스칼 케이스로 작성합니다.<br>

<br><br>

<img width="500" alt="image" src="https://github.com/BardsTale/vue_guide/assets/62861679/385c8e9f-182f-4ad9-8ff4-40cb0e3980a4">


> **세 번째**, 베이스 컴포넌트 이름은 Base, App, V 등 세 가지 접두사로 시작한 합성어여야 합니다.<br>
어플리케이션 고유의 스타일과 규칙을 적용하는 베이스 컴포넌트를 작성할 경우 용도의 구분을 위해 정해진 세 가지 접두사만을 사용하여야 합니다.<br>

<br><br>

![image](https://github.com/BardsTale/vue_guide/assets/62861679/e338076e-4274-4562-bee6-a55fc1ffa572)

> **네 번째**, 싱글 인스턴스 컴포넌트 이름은 반드시 The 접두사로 시작한 합성어여야 합니다.<br>
한 페이지당 하나의 활성 인스턴스만을 갖는 컴포넌트는 오직 하나의 인스턴스만을 있을 수 있음을 표시하도록 The 접두사로 시작해야 합니다.<br>

<br><br>


![image](https://github.com/BardsTale/vue_guide/assets/62861679/4ba48afe-21ee-4a73-b6c9-ad0e230d935a)

> **다섯 번째**, 밀접하게 연관된 부모, 자식간의 컴포넌트 이름은 접두사로 부모 컴포넌트 이름을 사용해야 합니다.<br>
이는 알파벳 순으로 정렬하는 코드 에디터에서 순서가 나란히 유지되어 부모, 자식관의 연관 관계와 가독성을 높여줍니다.<br>

<br><br>


![image](https://github.com/BardsTale/vue_guide/assets/62861679/43b2daa9-be4f-4f18-9b24-d3b0c178e1a0)

> **여섯 번째**, 컴포넌트 이름의 단어 순서는 상위 수준의 단어(대부분이 자주 또 일반적으로 사용하는 단어)로 시작하고 설명을 나타내는 단어로 끝나야 합니다.<br>
예를 들면 SearchButtonClear.vue 와 같은 형식의 사용을 권장하며 이는 코드 에디터의 정렬 및 기능별 분류에 도움이 됩니다.<br>

<br><br><br><br>






### 2. 파일 내부 컴포넌트 명명 규칙

파일 내부에서 컴포넌트를 사용 시 세 가지 핵심 명명 규칙이 있습니다. 
<br><br>
 
![image](https://github.com/BardsTale/vue_guide/assets/62861679/186225c5-236b-44be-9a9e-2df1364f89c9)

> **첫 번째**, 파일 내부에서 컴포넌트를 기술 할 때 파스칼 케이스로 Import 하고 뷰 인스턴스 등록 시 케밥 케이스(kebab-case)로 사용합니다.<br>
파스칼 케이스가 케밥 케이스보다 장점이 많지만 템플릿 내부에서 사용 시 DOM 템플릿일 경우 HTML은 대소문자를 구분할 수 없으므로 범용성이 큰 케밥 케이스를 사용하도록 합니다.<br>
**(하지만 JS에서 파스칼 케이스는 인스턴스를 가질 수 있는 객체를 의미하는 표기법이므로 뷰 컴포넌트 또한 그 의미가 같으므로 파스칼 케이스의 자기서술적인 장점이 더 크긴 합니다.)**<br>

<br><br>


![image](https://github.com/BardsTale/vue_guide/assets/62861679/5ca520fc-5fe6-4580-aabd-c8af6b1aee79)

> **두 번째**, 템플릿 내부에서 컴포넌트를 사용 시 내용이 없는 컴포넌트는 self-closing 처리를 해야 합니다.<br>
Slot이 들어가는 컴포넌트나 DOM 템플릿에서는 self-closing 하여선 안됩니다.<br>

<br><br>


![image](https://github.com/BardsTale/vue_guide/assets/62861679/2a0b392d-f0c4-4392-9fd2-44436bcfdf16)

> **세 번째**, 컴포넌트명은 약어보다 전체 단어를 사용하여 작성합니다.<br>
코드 에디터는 자동 완성 기능을 제공하므로 긴 이름에 대한 부담이 적고 이에 비해 정확한 단어가 제공하는 이름의 명확성이 주는 자기 서술성의 효과가 더 크므로 전체 단어를 사용합니다.<br>
따라서 굳이 약어를 쓸 경우, 일반적으로 자주 쓰이며 중복이 되지 않는 약어를 사용합니다.<br>

<br><br><br><br>




### 3. 컴포넌트와 인스턴스의 일관성 있는 옵션 순서

컴포넌트와 인스턴스 옵션의 순서는 용도에 따라 일관성 있게 정렬되어야 합니다.<br>
다음은 Vue 공식 스타일 가이드에서 권장되는 기본 순서입니다. 유형 별로 나누어 놓았으므로 플러그인에서 추가한 속성들 역시 이에 맞추어 정렬하면 됩니다.
<br><br><br>


>1 - 전역 인지(Global Awareness) (컴포넌트 바깥의 지식을 필요로 하는 옵션)
```
name
```

>2 - 템플릿 변경자(Template Modifiers) (템플릿 컴파일 방식 변경)
```
delimiters
```

>3 - 템플릿 종속성(Template Dependencies) (템플릿에서 사용된 에셋)
```
components
directives
```

>4 - 구성, 합성(Composition) (속성들을 옵션에 병합)
```
extends
mixins
provide/inject
```

>5 - 인터페이스(Interface) (컴포넌트에 대한 인터페이스)
```
inheritAttrs
props
emits
```

>6 - 컴포지션 API(Composition API) (Composition API 사용을 위한 진입점)
```
setup
```

>7 - 로컬 상태(Local State) (로컬 반응형 속성)
```
data
computed
```

>8 - 이벤트(Events) (반응형 이벤트에 의해 트리거된 콜백)
```
watch
```

>9 - 라이프사이클 이벤트들 (호출된 순서)
```
beforeCreate
created
beforeMount
mounted
beforeUpdate
updated
activated
deactivated
beforeUnmount
unmounted
errorCaptured
renderTracked
renderTriggered
```

>10 - 비-반응형 속성(Non-Reactive Properties) (반응성 시스템과 무관한 인스턴스 속성)
```
methods
```

>11 - 렌더링(Rendering) (컴포넌트 출력에 대한 선언적 설명)
```
template/render
```
<br><br><br><br>


### 4. 컴포넌트 요소 속성(디렉티브 등) 순서

디렉티브와 같이 컴포넌트에 바인딩하는 요소에 대한 순서 또한 유형 별로 일관성 있게 선언하면 개발 시 사용자지정 속성 및 디렉티브를 새롭게 추가할 때 도움이 됩니다.<br>
다음은 Vue 공식 스타일 가이드에서 권장되는 기본 순서입니다.
<br><br><br>


>1 - 정의(Definition) (컴포넌트 옵션 제공)
```
is
```

>2 - 리스트 렌더링(List Rendering) (동일한 요소의 여러 변형 생성)
```
v-for
```

>3 - 조건(Conditionals) (요소가 렌더링/표시될 지 여부)
```
v-if
v-else-if
v-else
v-show
v-cloak
```

>4 - 렌더 수식어(Render Modifiers) (요소 렌더링 방식 변경)
```
v-pre
v-once
```

>5 - 전역 인지(Global Awareness) (컴포넌트 바깥의 지식을 필요로 하는 옵션)
```
id
```

>6 - 고유 속성(Unique Attributes) (고유 값이 필요한 속성)
```
ref
key
```

>7 - 양방향 바인딩(Two-Way Binding) (바인딩 및 이벤트 결합)
```
v-model
```

>8 - 기타 속성(Other Attributes) (모든 지정되지 않은 바인딩, 언바인딩 속성)


>9 - 이벤트(Events) (컴포넌트 이벤트 리스너)
```
v-on
```

>10 - 컨텐츠(Content) (요소의 컨텐츠를 재정의함)
```
v-html
v-text
```
<br><br><br><br>


### 5. Prop과 Emit 정의

![image](https://github.com/BardsTale/vue_guide/assets/62861679/ba9ab4d1-87ec-40db-acca-98fa1949d7b9)

Prop은 Vue 인스턴스에서 props에 기술하며 emit은 emits에 기술합니다.<br>
이때 emit은 배열 방식을 사용하여도 괜찮지만 Prop은 배열 방식이 아닌 객체 방식으로 최대한 상세하게 선언해야 하며 최소한 **type**은 명시하여야 합니다.
<br><br><br>


### 6. Prop 명명 규칙

![image](https://github.com/BardsTale/vue_guide/assets/62861679/ae348694-3e80-4320-865b-bd8149bb16e1)

prop명은 선언 중에는 항상 카멜 케이스를 사용해야 하지만, 템플릿 및 JSX에서는 케밥 케이스를 사용해야 합니다.<br>
이는 단순한 이유입니다. JS에서 선언 시 카멜 케이스가 자연스럽고 HTML에서는 케밥 케이스만이 존재 할 수 있기 때문입니다.
<br><br><br>


### 7.  v-for에 key 지정

![image](https://github.com/BardsTale/vue_guide/assets/62861679/c41b7879-4fef-4c7e-b964-3a8fb6bbb7ad)

v-for 사용 시 반드시 key를 바인딩 시켜야 합니다.<br>
이는 단순히 반복된 엘리먼트를 구분하기 위해서가 아닌 Vue에서 가상 DOM의 작동 원리인 [in place patch](https://goodteacher.tistory.com/525) 전략에 따라 반복된 엘리먼트의 하위 트리 구조를 유지하기 어렵기 때문에 반드시 추가하여야 합니다.
<br><br><br>


### 8.  v-if와 v-for 동시 사용 피하기

![image](https://github.com/BardsTale/vue_guide/assets/62861679/5bb2db65-e551-4070-b779-746a5d165d50)

v-for를 쓴 엘리먼트에 절대 v-if를 사용하여선 안됩니다.<br>
2.x 버전에선 v-for가 우선순위를, 3.x 버전에선 v-if가 우선순위를 가지며 이는 개발자로 하여금 큰 혼돈을 줍니다.<br>
따라서 원하는 우선순위 의도에 따라 v-if를 v-for 내부에 둘 지 혹은 외부에서 감싸 놓을 지를 명확히 구분해서 사용합시다. 
<br><br><br>


### 9.  템플릿의 간단한 표현 추구

![image](https://github.com/BardsTale/vue_guide/assets/62861679/9c9a398a-2d67-4ac4-8847-bc9447aed877)

템플릿에서 복잡한 표현식을 사용하는 것은 직관적이지 않아 해석에 악영향을 줍니다.<br>
함수형 프로그래밍 패러다임에 따라 표현식에선 값을 계산하는 방법을 서술하는 것이 아닌 무엇을 표시하려는지 설명해야 합니다.<br>
따라서 복잡한 표현식이 필요한 경우 computed에 선언을 합니다.<br>
(* 참고로 computed는 vue 반응성 시스템에 따라 종속성 검사를 거친 후 실행 됩니다. [관련 링크](https://v2.vuejs.org/v2/guide/reactivity.html#How-Changes-Are-Tracked))
<br><br><br>


### 10.  간단한 computed

<img width="1566" alt="image" src="https://github.com/BardsTale/vue_guide/assets/62861679/05abe772-5532-42d5-9c30-94830c7863c9">


coumputed 속성은 복잡해지지 않도록 여러 개의 간단한 computed 속성으로 분할하여야 합니다.<br>
작게 분류된 computed 속성은 조합 시 보다 직관적이며 요구사항 변경에 따른 리팩토링에 대해서도 유연합니다.<br>
<br>
이에 관하여 추가로 핵심 장점 세 가지를 서술하자면 다음과 같습니다.
<br>

* **테스트 하기 쉬움(Easier to test)**<br>
다른 변수와의 종속성이 거의 없는 매우 간단한 표현식만 있으면 작동여부를 테스트하는 데 수월합니다.<br>

* **읽기 쉬움(Easier to read)**<br>
명칭을 직관적이게 하여 본인 및 다른 개발자가 명칭만으로도 해석이 가능하고 파악할 수 있는 것이 좋습니다. 절차적이지 않고 선언적인 프로그래밍을 지향해야합니다.<br>

* **변화하는 요구사항에 더 적응(adaptable)하기 좋음**<br>
computed를 최종적인 목적을 지닌 하나의 값보다 기능을 잘게 쪼개어 조합하는 것이 변화에 유연하고 재사용성이 좋습니다.<br>
<br><br><br>


### 11. 디렉티브 약어(Directive shorthands) 일관성 유지

![image](https://github.com/BardsTale/vue_guide/assets/62861679/07bed098-439a-47f2-9a91-f8383f2a840b)

디렉티브 약어는 모두 쓰거나, 쓰지 말아야 합니다. (: 는 v-bind:, @ 는 v-on:, # 는 v-slot)<br>
약어의 혼용은 개발자로 하여금 혼란을 가하게 되므로 혼용은 지양해야 합니다.<br>
<br><br><br>


### 12. 부모-자식 컴포넌트 통신 시 this.$parent나 props 변경 대신, props down, event up 사용.

<img width="1389" alt="image" src="https://github.com/BardsTale/vue_guide/assets/62861679/8d06d640-f5d1-4a18-8b92-b285b69931ac">


Vue 작동 원리에 따르면 이상적인 Vue 어플리케이션은 props down, events(emits) up입니다.<br>
이 규칙을 유지하면 컴포넌트를 훨씬 쉽게 이해가 가능하며 디버깅이 쉬워집니다.<br>
<br>
그러나 readonly인 prop을 변경하거나 this.$parent를 접근하여 사용한다면 훨씬 코드 작성이 단순화 될 수도 있습니다.<br>
그렇지만 작동 원리에 위배된 이러한 단기적인 편리함은 문제점을 야기 시킬 수 있으므로 지양하여야 합니다.<br>
<br><br><br>


### 13. 직접적으로 DOM 접근이 필요한 경우, Real DOM 접근이 아닌 ref를 사용.

![image](https://github.com/BardsTale/vue_guide/assets/62861679/142387d3-0396-45ba-b0f3-7f3609a812b6)


Vue는 가상 DOM(Virtual DOM)을 사용하기 때문에 Real DOM을 접근하여 사용 시 가상 DOM의 이점이 잃게 되며<br>
이로 인해 [비동기 업데이트 큐(Async update queue)](https://github.com/BardsTale/vue_guide/blob/main/vue_queue.md)에도 문제가 생길 수 있습니다.<br>
따라서 querySelector나 getElementBy... 이 아닌 ref를 사용하여 DOM에 접근하는 것을 권장합니다.<br>
<br><br><br>



### 14.  DOM 상태에 따라 개발하지 말고 구성 요소(data, computed)의 상태에 따라 개발.

![image](https://github.com/BardsTale/vue_guide/assets/62861679/7cbd90fa-f141-4f5d-8cb2-193eb228a02f)

전통적인 프론트엔드 UI 개발 시 직접 DOM 요소에 접근하여 요소의 상태를 판별해서 개발하는 경우가 많지만<br>
Vue에서는 구성 요소(**data**, **computed**)의 상태에 따라 개발하는 것이 좋습니다.<br>
<br>
왜냐하면 Vue에서는 가상 DOM을 사용하기 때문에 [비동기 업데이트 큐(Async update queue)](https://github.com/BardsTale/vue_guide/blob/main/vue_queue.md)로 인하여<br>
DOM의 상태가 업데이트 되는 시점이 일정치 않습니다.<br>
따라서 직접적인 DOM 요소의 상태보다는 data나 computed 요소를 바인딩 시키고 이 반응형 값에 따라 로직을 짜는 것이 권장되며<br>
[vue 트랜지션](https://v3.ko.vuejs.org/guide/transitions-overview.html#%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%84%89%E1%85%B3-%E1%84%80%E1%85%B5%E1%84%87%E1%85%A1%E1%86%AB-%E1%84%8B%E1%85%A2%E1%84%82%E1%85%B5%E1%84%86%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%89%E1%85%A7%E1%86%AB-%E1%84%90%E1%85%B3%E1%84%85%E1%85%A2%E1%86%AB%E1%84%8C%E1%85%B5%E1%84%89%E1%85%A7%E1%86%AB)을 사용하는 경우,
[트랜지션 훅](https://v3.ko.vuejs.org/guide/transitions-enterleave.html#javascript-%E1%84%92%E1%85%AE%E1%86%A8)을 사용하는 것이 좋습니다.<br>
<br>
그러나 불가피하게 DOM 요소에 직접적인 접근을 해야하는 경우 [**nextTick 콜백**](https://v3.ko.vuejs.org/api/instance-methods.html#nexttick)을 통해 해결할 수 있습니다.
