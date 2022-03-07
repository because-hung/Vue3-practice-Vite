<script setup>
import { computed, ref } from "vue";
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


</script>
<template>
<h2>Practice template</h2>
<h3>com:{{com}}</h3>
<button @click="clickA(false)">enterA</button>
<h2>enterA {{status}}</h2>
<button @click="clickA(true)">enterB</button>
<h2>enterB {{status}}</h2>
</template>