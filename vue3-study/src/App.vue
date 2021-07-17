<template>
  <div class="name">
    <!-- 2. greeting이라는 함수를 통해 'Hello'라는 문자열 넣어보기 -->
    <!-- 함수로 접근을 할 때에는 함수명 뒤에 ()를 적어줘야 한다. -->
    {{ greeting() }}
  </div>
</template>

<script>
export default {
  setup() {
    const name = "Junsung";
    // 1. 함수 정의하기
    // 1-1. setup 함수 내에 greeting이라는 이름의 화살표 함수를 만든다.
    const greeting = () => {
      // 1-2. greeting 함수에서 'Hello'라는 값을 return해준다.
      return 'Hello';
    }
    return {
      name,
      // 1-3. setup 함수에서 greeting 함수를 return해줌으로써 template에 접근할 수 있게 된다.
      greeting,
    };
  }
}
</script>

<style>
  .name {
    color: red;
  }
</style>