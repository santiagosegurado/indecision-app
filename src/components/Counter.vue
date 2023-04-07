<template>
  <h2>{{ customTitle }}</h2>
  <p>{{ count }} <sup>{{ exponential }}</sup> = {{ powComputed }} </p>
  <button @:click="plus">
    +1
  </button>
  <button @:click="substract">
    -1
  </button>
</template>

<script>
export default {
  name: "Counter",
  // Atributos
  props: {
    start: {
      type: Number,
      required: true,
      default: 0,
      validator: (value) => {
        return value > -1;
      }
    },
    title: String,
  },
  data() {
    return {
      count: this.start,
      exponential: 2,
    }
  },
  methods: {
    pow(){
      return Math.pow(this.count, this.exponential);
    },
    plus(){
      this.count++;
    },
    substract(){
      this.count--;
    }
  },
  // Las opciones computadas quedan en cache, es decir que solo se recargan cuando cambian 
  computed:{
    powComputed(){
      return Math.pow(this.count, this.exponential)
    },
    customTitle() {
      return this.title || 'Counter';
    }
  }
}
</script>

<style>
  button{
    background-color: #64B687;
    color: white;
    border: 1px solid white;
    cursor: pointer;
    margin: 0px 5px;
    padding: 5px 15px;
    transition: all 0.3s ease-in-out;
    border-radius: 5px;
  }

  button:hover{
    background-color: #5aa67b;
  }
</style>