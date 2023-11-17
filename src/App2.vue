<template>
  <div>
    <h1>{{ count }}</h1>
    <button v-on:click="addNumber(1)">증가</button>
    <button v-on:click="minusNumber">감소</button>
    <button v-on:mouseover="addNumber(10)">마우스 오버 10 증가</button>

    <hr>

    <h2>{{ message1 }}</h2>
    <button @click="gretting">인사하기</button>
    <button @click="goodbye">작별하기</button>
    <div @click="getMousePosition" class="box"></div>

    <hr>

    <h2>{{ message2 }}</h2>
    <button @click="plusNumber($event, 10)">10 더하기</button>
    <button @click="plusNumber($event, 100)">100 더하기</button>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      count: 0, 
      message1: "",
      message2: ""
    }
  },
  methods: {
    /* 사용할 함수(메소드) 작성하는 위치 */
    addNumber(value) {
      // console.log("add Number");
      // this.count++;

      this.count += value;
    },
    // 화살표 함수 사용시 this 값 감지 못해 에러남 -> 사용 불가
    // minusNumber: () => {
    //   console.log(this); // undefined
    //   this.count--;
    // }
    minusNumber() {
      this.count--;
    },
    gretting() {
      this.message1 = "안녕하세요";
    },
    goodbye() {
      this.message1 = "잘가~~";
    },
    getMousePosition(event) {
      console.log(event);
      this.message1 = `마우스의 위치는 X:${event.pageX}, Y:${event.pageY} 입니다.`;
    },
    plusNumber(event, value) {
      event.pageX
      this.message2 = `마우스 좌표 ${event.pageX}와 + ${value}는 ${event.pageX + value}입니다.`;
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

button {
  width: 100px;
  height: 100px;
  font-size: 24px;
}

.box {
  width: 300px;
  height: 300px;
  background-color: salmon;
}
</style>
