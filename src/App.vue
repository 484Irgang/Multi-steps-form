<script>
  import PersonalInfo from "./components/PersonalInfo.vue"

  export default{
    components: {PersonalInfo}
  }
</script>

<template>
  <div class="container">
    <PersonalInfo/>
  </div>
</template>

<style scoped>
  .container{
    width: 100%;
    height: 100vh;
    overflow: hidden;
    padding: 2%;
    background-color: #EEF5FF;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
      }
  .container > div{
    width: 100%;
    max-width: 1100px;
    height: 100%;
    max-height: 600px;
    background-color: white;
    border-radius: 14px;
    box-shadow: 4px 6px 30px -20px rgba(0, 0, 0, 0.5);
  }
</style>
