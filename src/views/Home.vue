<template>
  <div class="nav">
    <h1>Home</h1>
    <p class="id" ref="p">my name is {{ name }} and my age is {{ age }}</p>
  </div>
  <div class="input">
    <input type="text" v-model="name" />
    <input type="number" v-model="age" />
  </div>
  <div class="search">
    <input type="text" v-model="search" />
    <p> search term: {{ search }}</p>
    <div v-for="name in filteredNames" :key="name">{{ name }}</div>
  </div>
  <div class="age">
    <button @click="age--">decreace age</button>
    <button @click="age++">increace age</button>
  </div>
  <div class="home">
    <button @click="handleClick">Click</button>
    <!-- <button @click="handleClickTwo">Change name/age</button> -->
  </div>
</template>

<script>
import { ref, computed } from "vue";
export default {
  name: "Home",
  setup() {
    const p = ref(null);
    const name = ref("seif");
    const age = ref(26);
    const isOriginalText = ref(true);
    const search = ref("");
    const names = ref(["seif", "ahmed", "ali", "mohamed", "khaled"]);
    const handleClick = () => {
      console.log(p, p.value);
      p.value.classList.toggle("test");
      if (isOriginalText.value) {
        p.value.textContent = "i train gym and i love it";
      } else {
        p.value.textContent = `my name is ${name.value} and my age is ${age.value}`;
      }
      isOriginalText.value = !isOriginalText.value;
    };
    // const handleClickTwo = () => {
    //   name.value = "ahmed";
    //   age.value = 27;
    //   if (isOriginalText.value) {
    //     p.value.textContent = "i train gym and i love it";
    //   } else {
    //     p.value.textContent = `my name is ${name.value} and my age is ${age.value}`;
    //   }
    //   isOriginalText.value = !isOriginalText.value;
    // };
    const filteredNames = computed(() => {
      return names.value.filter((name) => name.includes(search.value));
    });
    return { p, handleClick, name, age, filteredNames, search };
  },
};
</script>

<style scoped>
.search {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 10px;
  width: 100%;
  height: 100%;
  margin-top: 20px;
}
.age {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  gap: 10px;
  width: 100%;
  height: 100%;
  margin-top: 20px;
}
.age button {
  background-color: lightcoral;
  color: #fff;
  border: none;
  height: 100%;
  width: 60%;
  border-radius: 5px;
  padding: 10px 20px;
  font-size: 1rem;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
}
.age button:hover {
  background-color: black;
}
.input {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 10px;
  width: 100%;
  height: 100%;
  margin-top: 20px;
}
input {
  padding: 10px;
  border-radius: 10px;
  border: 1px solid #333;
  width: 70%;
  height: 100%;
  font-size: 1rem;
  font-family: "Arial", sans-serif;
  transition: all 0.3s ease;
  outline: none;
  cursor: pointer;
  border: 1px solid #333;
}
input:hover {
  background-color: lightblue;
}
.nav {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 10px;
  width: 100%;
  height: 100%;
  background-color: black;
  color: #fff;
  border-radius: 10px;
}
.nav h1 {
  text-align: center;
  font-size: 2rem;
  font-weight: bold;
  color: #4d4c4c;
  font-family: "Arial", sans-serif;
  transition: all 0.3s ease;
}
.nav h1:hover {
  color: #fff;
}
.nav p {
  color: #4d4c4c;
  transition: all 0.3s ease;
}
.nav p:hover {
  color: white;
}
.id {
  font-size: 1rem;
  font-weight: bold;
  color: #fff;
  font-family: "Arial", sans-serif;
}
.home {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  width: 100vw;
}
p {
  text-align: center;
  font-size: 2rem;
  font-weight: bold;
  color: #333;
}
button {
  margin-top: 20px;
  padding: 10px 20px;
  font-size: 1rem;
  font-weight: bold;
  color: #fff;
  background-color: #007bff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: all 0.3s ease;
}
button:hover {
  background-color: #0056b3;
}
.test {
  color: lightcoral;
  text-align: center;
  font-size: 2rem;
  font-weight: bold;
  transition: all 0.3s ease;
}
.test:hover {
  color: blue;
}
</style>
