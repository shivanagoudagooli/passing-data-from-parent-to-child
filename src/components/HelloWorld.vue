<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <child :names="names"></child>
    <p>
      i am from child component ,{{myName}}
    </p>
  </div>
</template>

<script>
import child from './child.vue'
import {Eventbus} from '../components/Eventbus.js';
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return {
      names:[
        {name :"shiva"},
        {name1:"raja"},
        {name2:"varun"}],
        myName:""
    }
  },
  components:{
    child
  },
  created(){
    Eventbus.$on("btn", this.getMyName);
    this.getMyName;
  },
  methods:{
    getMyName(name){
      this.myName = name;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
