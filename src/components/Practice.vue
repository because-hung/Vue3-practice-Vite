<script setup>
import { computed, reactive, ref } from "vue";

const imgList = reactive([
    {
    img1: 'src/assets/test/btn00.png',
    img2: 'src/assets/test/btn01.png',
},
    {
    img1: 'src/assets/test/btn01.png',
    img2: 'src/assets/test/btn02.png',
},
    {
    img1: 'src/assets/test/btn02.png',
    img2: 'src/assets/test/btn03.png',
},
 {
    img1: 'src/assets/test/btn03.png',
    img2: 'src/assets/test/btn00.png',
},

])
let aaa = [22,15,85,94,45,66]


const filtered = aaa.filter((item, index)=>{
    console.log('item', item[index])
    return item < 50
})
 console.log(filtered)
// const obj = {
//     'id':'01',
//     'name':'robert'
// };

// const aaa = Object.values(obj);
// console.log(aaa);

function getUrl(index){
  return new URL(`../assets/test/btn0${index}.png`, import.meta.url)
}



let obj = {value: 'before'}
console.log('before:', obj) // 應該要是 {value: 'before'}
obj.value = 'after'
console.log('after:', obj)

//work restart
let status = ref(true)
const clickA = (A) => {  //用同一個 func 操作  //給狀態boolean參數傳入去判斷 
    status.value = A;
}


const com = computed(() => {
    let result = 0
    console.log('st', status)
if(status.value == true){
     result = 1
    
}else{
      result =  2
}
return result
})

const anFlag = ref(false)

function toAN(){
    console.log('an click')
    anFlag.value = true
    setTimeout(() => {
    anFlag.value = false
  }, 1300)
}


</script>
<template>
<div class="container">
    <h2 @click='toAN()'>test animation</h2>
    <div v-if="anFlag" class="box displayB">copied</div>
    <h2 v-if='false'>test vite require</h2>
<ul v-if='false' v-for='(item, index, i) in imgList' :key='i'>
    <li class="testImg"><img :src="item.img1" alt=""></li>
</ul>
</div>
<section v-if='false'><h2>Practice template</h2>
<h3>com:{{com}}</h3>
<button @click="clickA(false)">enterA</button>
<h2>enterA {{status}}</h2>
<button @click="clickA(true)">enterB</button>
<h2>enterB {{status}}</h2></section>

</template>

<style scoped>
.box{
    margin: 0 auto;
    background: black;
    width: 120px;
    height: 50px;
    color: white;
    border-radius: 20px;
}
.testImg > img{
width: 50px;
height: 50px;
}

.displayB{
  animation: displayB 1.5s;

}

@keyframes displayB {
  0% { opacity: 0.2;}
    50% { opacity: 1;}
    100% { opacity: 0.2;}
}
      

</style>