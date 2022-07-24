<script setup>
import { computed, reactive, ref } from "vue";

// thousand

let thA = "222122122.7812" // 222,122,122.78
let thB = Number(thA).toFixed(2).replace(/(\d)(?=(\d{3})+\.)/g, '$1,') //使用正则替换，每隔三个数加一个','

console.log(thB)


// copy

function copyWrite(){


const range = document.createRange()
const texts = document.querySelector('.allcopy')
  range.selectNode(texts)
  // 取得 Selection 物件
const selection = window.getSelection()
  selection.addRange(range)
document.execCommand("copy")
}

// two box

const boxFlag = ref(false)

function openBox(){
    boxFlag.value = !boxFlag.value
}

//


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

const aryAA = [1,2,3]
const aryBB = [2,3,4]

const anFlag = ref(false)

 const testNum = ref(1)
    function clickAA() {
      testNum.value = 2
    }
    function clickBB() {
      testNum.value = 1
    }

function toAN(){
    const btnDom = document.querySelector('.imgB')
btnDom.style.zIndex = 0
    console.log('an click')
    anFlag.value = true
    setTimeout(() => {
    anFlag.value = false
    btnDom.style.zIndex = -1
  }, 1300)
}


</script>
<template>
<div class="container">
    <h2 @click="openBox()">test box</h2>
    <!-- rotate arrow -->
    <div class="oner">
        <div class="oBoxA"> <img  :class="{'openArrow': boxFlag }" class="arrowDown" src="../assets/test/arrowDown.png" alt=""></div>
        <div class="oBox oBoxB" v-if='boxFlag'></div>
       
    </div>
    <h2>test copy</h2>
    <div class="allcopy" >
        <h4 class="billNum">billNo: 123456489797981623</h4>
        <div class="title">wang</div>
        <span class="todo">live coding</span>
        <button @click="copyWrite()">copy memememe</button>
    </div>

    <h2 @click='toAN()' class="anTitle">test animation</h2>
    <h2>{{testNum}}</h2>
      <div class="group">
    <img @click="clickAA()" class='imgA imgC' src="@/assets/test/btn04.jpg" alt="">
    <img @click="clickBB()" class='imgB imgC' src="@/assets/test/btn05.jpg" alt="">
    <p></p>
    <p></p>
    </div>
    <div class="div"  v-if='testNum === 1'>
    <ul v-for='(item, i) in aryAA' :key='i'>
        <li>{{item}}</li>
    </ul>
    </div>
    <div class="div" v-if='testNum === 2'>   
    <ul v-for='(item, i) in aryBB' :key='i'>
        <li>{{item}}</li>
    </ul>
    </div>
    <div class="noData" v-if='(testNum == 1 && aryAA.length == 0) || (testNum == 2 && aryBB.length == 0)'>
        <h2>hello world</h2>
    </div>
    <div class="testBall">123<div class="ball"></div></div>
  
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
.arrowDown{
    width: 50px;
    height: 20px;
    position: relative;
    top: 40px;
    left: 100px;
    margin: 20px 0px;
}
.openArrow{
  transform: rotate(180deg);
}
.oBox{
    width: 300px;
    height: 100px;
    background: red;
}

.oBoxA{
    width: 300px;
    height: 100px;
    border: 1px blue solid;
    box-shadow: 1px 1px;
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
    /* border-radius: 10px; */

}

.oBoxB{
       border: 1px red solid;
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
    /* border-radius: 10px; */

}
.imgC{
    width: 250px;
    height: 80px;
    margin-right: 5px;
}

.imgB{
    position: relative;
    left: -75px;
    }
.anTitle{
    position: relative;
}
.testBall{
    position: relative;
width: 150px;
    
}
.ball{
    position: absolute;
    width: 12px;
    height: 12px;
    background: red;
    border-radius: 100%;
    right: 0;
    top: 0;
}
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