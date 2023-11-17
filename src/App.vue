<script>
export default {
  name: 'App',
  data() {
    return {
      animal: "Monkey",
      food: "apple",
      alertMessage: "<h2>경고!!!</h2>",
      subscribeHTML: `<button onclick="document.querySelector('body').style.background = 'red'">구독하기</button>`,
      imageSource: "https://cdn.pixabay.com/photo/2023/10/16/07/55/animal-8318650_1280.jpg",
      naverUrl: "https://www.naver.com",
      age: 18,
      display: false,
      animals: [ "monkey", "rat", "dog", "lion" ],
      users: [
        { name: "scalper", job: "developer", gender: "male", skills: [ "html", "css", "javascript" ]},
        { name: "john", job: "designer", gender: "male", skills: [ "html", "css", "javascript" ]},
        { name: "jessi", job: "pm", gender: "female", skills: [ "html", "css", "javascript" ]}
      ]
    };
  }
};
</script>

<template>
  <h1>Hello {{ animal }}</h1>
  <h2>원숭이는 {{ food }}를 좋아합니다</h2>

  <!-- <h3 v-text="food"></h3> -->
  <input type="text" v-model="food">

  <!-- <div>{{ alertMessage }}</div> -->
  <div v-html="alertMessage"></div>
  <div v-html="subscribeHTML"></div>

  <P>
    <img :src="imageSource" alt="random">
    <br>
    <a :href="naverUrl">naver</a>
  </P>

  <div>
    <a :href="food">{{ food }}</a>
  </div>

  <hr />

  <h2 class="green">원숭이는 {{ food }}를 좋아합니다</h2>
  <!-- <h2 v-bind:class="{ 클래스 : 조건(참/거짓) }"></h2> -->
  <h2 v-bind:class="{ red: food === 'apple', 'not-good': food === 'rice' }">원숭이는 {{ food }}를 좋아합니다</h2>

  <hr />

  <h2>당신의 나이는 {{ age }} 입니다</h2>
  <h3 v-if="age > 18">당신은 어른입니다</h3>
  <h3 v-else-if="age > 13 && age <= 18">당신은 청소년입니다</h3>
  <h3 v-else>당신은 어린이입니다</h3>

  <!-- v-show 디렉티브는 속성값이 false일때 dispaly: none -->
  <h2 v-if="display">(if)보입니다!!</h2>
  <h2 v-show="display">(show)보입니다!!</h2>

  <h2>{{ animals }}</h2>
  <h2 v-for="animal in animals" :key="animal">{{ animal }}</h2>
  <h2 v-for="(animal, index) in animals" :key="index">{{ animal }} 인덱스 :: {{ index }}</h2>
  <ul>
    <li v-for="(user, index) in users" :key="index">
      이름은 {{ user.name }}이고 직업은 {{ user.job }}
      <p v-for="skill in user.skills" :key="skill">{{ skill }}</p>
    </li>
  </ul>

  <!-- <h2 v-for="(animal, index) in animals" :key="index">{{ animal }} 인덱스 :: {{ index }}</h2> -->
  <!-- 위 코드에서 monkey 출력 안되게 할 때 -->
  <!-- v-for와 v-if는 한 태그 내에서 동시 사용 불가능 -->
  <!-- <template></template> 사용 -->
  <template v-for="(animal, index) in animals" :key="index">
    <h2 v-if="animal !== 'monkey'">{{ animal }} 인덱스 :: {{ index }}</h2>
  </template>

</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

input {
  font-size: 20px;
}

img {
  width: 100px;
  height: 100px;
}

.green {
  color: green;
}

.red {
  color: red;
}

.not-good {
  text-decoration: line-through;
}
</style>
