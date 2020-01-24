<template>
<div>
    <div v-for="(i,index) in names" v-bind:key="index">
        <table style="display:flex;width:100px;margin-left:50%;" >
            <tr>
                <td>{{i.name}}
                  {{i.name1}}
                {{i.name2}}</td>
            </tr>
        </table>
    </div><br>
    <br>
    <div :class = "[apply ? 'addColor' :'addColor1']">
       UserName : <input type="text" value="shiva" id="name" />
       <button type="button" v-on:click="getName">click</button>
    </div>
</div>
</template>
<script>
import {Eventbus} from '../components/Eventbus.js';
export default {
    props:["names"],
    data(){
        return{
            UserName :'',
            apply:false
        }
    },
    mounted(){
        this.callApi().then((data) =>{
            console.log(data)
        });
    },
    methods:{
        getName(){
            let name = document.getElementById("name").value;
            this.UserName = name;
            this.apply = true;
            console.log(name);
            Eventbus.$emit("btn",name);
        },
        callApi:function(){
            let a =9;
            let b= 9;
            return new Promise((resolve,reject) =>{
                if(a==b){
                    resolve(" i am from promise");

                }else{
                    reject("false");
               }
            })
        }
    }
    
}
</script>
<style scoped>
.addColor{
    color:blue;
}
.addColor1{
    color: blueviolet;
}
table,td,tr{
    border: 1px solid blueviolet;
    padding: 10px;
    border-collapse: collapse;
    text-align: center;

}
</style>