<template>
  <!-- 1-4. template내에서 변수에 접근하려면 다음과 같은 방식으로 접근해야 한다. -->
  <!-- {{ 변수명 }} -->
  <!-- 2. style 안에 CSS 코드를 넣어서 글자색을 red로 바꿔보자. -->
  <!-- 2-1. div 태그에 클래스명을 설정해주고 -->
  <div class="name">{{ name }}</div>
</template>

<script>
// 1. composition API 사용
// 1-1 export default 내에 setup 함수를 만들고 그 안에서 필요한 로직을 작성
export default {
  setup() {
    // 1-2. 변수 등록
    const name = "Junsung";
    // setup 함수 내에서 object를 return한다.
    // 1-3. 사용하고자 하는 변수를 return해주면 template내에서 변수에 접근이 가능해진다.
    return {
      name
    };
  }
}
</script>

<style>
/* 2-2. '.클래스명{}' 으로 클래스를 호출해주고 색상 설정. */
/* 웹 브라우저에서 클래스명이 name인 div 태그안의 내용들의 색상이 빨간색으로 변경된 것을 확인할 수 있다. */
  .name {
    color: red;
  }
</style>