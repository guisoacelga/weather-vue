<template>
  <header>
    <h1>Find the current weather in any city!</h1>
  </header>
</template>


<script>
export default {
  name: "Header"
};
</script>

<style scoped>
header {
    height: 100px;
    background-color: lightblue;
    text-align: center;
    padding-top: 20px;
    box-shadow: 3px 3px 3px #ccc;
}

header h1 {
  font-size: 2rem;
  font-weight: bold;
  color: dodgerblue;
  margin: 0;
}
@media only screen and (max-width: 576px) {
 h1 {
    font-size: 0.75rem;
    margin-top: 60px;
  }
}
</style>