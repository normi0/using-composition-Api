<template>
  <h1>Home</h1>
  <p class="id" ref="p">my name is {{ name }} and my age is {{ age }}</p>
  <div class="input">
    <input type="text" v-model="name" />
    <input type="number" v-model="age" />
  </div>
  <div class="home">
    <button @click="handleClick">Click</button>
    <button @click="handleClickTwo">Change name/age</button>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  name: "Home",
  setup() {
    const p = ref(null);
    const name = ref("seif");
    const age = ref(26);
    const isOriginalText = ref(true);
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
    const handleClickTwo = () => {
      name.value = "ahmed";
      age.value = 27;
      if (isOriginalText.value) {
        p.value.textContent = "i train gym and i love it";
      } else {
        p.value.textContent = `my name is ${name.value} and my age is ${age.value}`;
      }
      isOriginalText.value = !isOriginalText.value;
    };

    return { p, handleClick, name, age, handleClickTwo };
  },
};
</script>

<style scoped>
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
  animation: fadeIn 0.3s ease;
}
h1 {
  text-align: center;
  font-size: 2rem;
  font-weight: bold;
  color: #333;
  font-family: "Arial", sans-serif;
  transition: all 0.3s ease;
}
h1:hover {
  color: #007bff;
}
.id {
  font-size: 1rem;
  font-weight: bold;
  color: #333;
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
