<template>
  <img v-if="img" :src="img" alt="bg" />
  <div class="bg-dark"></div>
  <div class="indecision-container">
    <input
      type="text"
      placeholder="Make me a question"
      v-model="question"
      
    />    
    <p>Remember to end with a question mark(?).</p>

    <div>
      <h2 v-if="question?.includes('?')">{{ question }}</h2>
      <h1>{{ answer }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return {
      question: null,
      answer: null,
      img: null,
    }
  },
  methods:{
    async getAnswer(){
      this.answer = 'Loading...';
      const resp = await fetch('https://yesno.wtf/api');
      const data = await resp.json();
      this.answer = data.answer.toUpperCase();
      this.img = data.image;
    }
  },
  // Watcher o Observable (se dispara cuando cambia la data)
  watch:{
    question(value){
      if(!value.includes('?')) return
      
      this.getAnswer();
    }
  }
};
</script>

<!-- el scoped sirve para que solo se aplique el css en este componente -->
<style scoped>
img,
.bg-dark {
  height: 100vh;
  left: 0px;
  max-height: 100%;
  max-width: 100%;
  position: fixed;
  top: 0px;
  width: 100vw;
}

.bg-dark {
  background-color: rgba(0, 0, 0, 0.4);
}

.indecision-container {
  position: relative;
  z-index: 99;
}

input {
  width: 250px;
  padding: 10px 15px;
  border-radius: 5px;
  border: none;
}
input:focus {
  outline: none;
}

p {
  color: white;
  font-size: 20px;
  margin-top: 0px;
}

h1,
h2 {
  color: white;
}

h2 {
  margin-top: 150px;
}
</style>
