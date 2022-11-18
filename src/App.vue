<template>
<!-- 引入样式 -->
<link rel="stylesheet" href="https://unpkg.com/element-ui/lib/theme-chalk/index.css">
<!-- 引入组件库 -->
<script src="https://unpkg.com/element-ui/lib/index.js"></script>
  <form action="" method="post">
    <form @submit.prevent="addOption">
    <input v-model="newOption">
    <button>Add</button>
   <ul>
    <li v-for="option in options" :key="option.id">
      {{ option.text }}
      <button @click="removeOption(option)" class="remove">X</button>
    </li>
  </ul>
  <form>
</template>

<script>
let abc='A'.charCodeAt()-1
console.log(typeof(abc))
let num=0
var address=[0,1,2,0,0,0,0,0,0,0,0]
export default {
  data(){
    return{
      newOption:'',
      options:[
        {id:++num,text:String.fromCodePoint(++abc)+'.'+"text1"},
        {id:++num,text:String.fromCodePoint(++abc)+'.'+"text2"}
      ]
    }
  },
  methods:{
    addOption(){
      address[num]=num;
      for(let i in address)//i为address下标
      {
        console.log("i="+i+" address[i]="+address[i]);
          if(i!=address[i])
          {
            num=Number(i);
            abc='A'.charCodeAt()+num-1;
            break;
          }
      }
      this.options.push({id:num,text:String.fromCodePoint(abc)+'.'+this.newOption})
      this.newOption=''
    },
    removeOption(option) {
      this.options = this.options.filter((t) => t !== option)
      for(let i in address){
        if(i==option.id) address[i]=0
      }
    }
  }
}
</script>

<style>
.remove{
  background-color: red;
  border: 0;
  color: white;
  height: 20px;
  width: 40px;
}

li{
  list-style-type: none;
}

</style>
