<template>
  <div>
    <router-view />
  </div>
</template>

<script>
export default {
  setup () {
    

    return {}
  }
}
</script>

<style scoped>
 #app {
  height: 100%;
  width: 100%;
  min-height: 100vh;
  min-width: 100vw;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: #f0f0f0;
  overflow: hidden;
  position: relative;
  padding: 20px;
  box-sizing: border-box;
  font-family: Arial, sans-serif;
  color: #333;
  font-size: 16px;
  line-height: 1.5;
  font-weight: 400;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  overflow: hidden;
  position: relative;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease-in-out;
  &:hover {
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
  }
 }
</style>
