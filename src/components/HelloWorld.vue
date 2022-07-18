<script setup>
import { computed, onUpdated, reactive, ref, watch } from "vue";
import Practice from './Practice.vue'

defineProps({
  msg: String,
});


const sum = ref(1);
//computed
const num = computed(() => {
  return sum.value * 2;
})

const changeSum = function(){
sum.value = 2
}

// watch(num,() => {
//   console.log(num);
// })


//data
const filterData =
  reactive(JSON.parse(localStorage.getItem("NumData"))) || reactive([]);
console.log(filterData);
const count = ref(0);
const data = reactive([
  {
    id: 1,
    user: "bob",
  },
  {
    id: 2,
    user: "bobber",
  },
  {
    id: 3,
    user: "rob",
  },
  {
    id: 4,
    user: "tom",
  },
  {
    id: 5,
    user: "toobee",
  },
  {
    id: 6,
    user: "eebob",
  },
  {
    id: 7,
    user: "deca",
  },
]);

//
//function

// const getStar = function (item) {
//   console.log(filterData);

//   const found = filterData.find((el) => {
//     return el.id === item.id;
//   });

//   if (!found) {
//     filterData.push(item);
//     localStorage.setItem("NumData", JSON.stringify(filterData));
//   }

//   console.log(filterData);
// };
// const cancelStar = function (item) {
//   const found = filterData.find((el) => {
//     return el.id === item.id;
//   });

//   if (found) {
//     filterData.splice(0, 1);
//     localStorage.setItem("NumData", JSON.stringify(filterData));
//   }

//   console.log(filterData);
// };

//work obj array

let foodData = reactive([
  {
    name: "tom17",
      
        country: "USA",
        id: "live",
        food: [
          {
            id:153252,
            cookie: "straw",
          },
          {
            id:744138,
            cookie: "banana",
          },
          {
            id:184312,
            cookie: "menlon",
          },
        ],
      
    
  },
  {
    name: "bay12",
 
        country: "CANA",
        id: "fixtures",
        food: [
          {
            id:102482,
            cookie: "straw",
          },
           {
            id:407782,
            cookie: "water",
          },
           {
            id:889782,
            cookie: "coden",
          },
           {
            id:482187,
            cookie: "beer",
          },
           {
            id:105538,
            cookie: "queen",
          },
        ],

  },
  {
    name: "Kom",
  
        country: "lorea",
        id: "finish",
        food: [
          {
            id:102738,
            cookie: "stw"
          },
           {
            id:780457,
            cookie: "kta"
          },
        ],

  },
  {
    name: "pp",
  
        country: "USAaaa",
        id: "others",
        food: [
          {
            id:102239,
            cookie: "sneak",
          },
          {
            id:402493,
            cookie: "fgh",
          },
          {
            id:987662,
            cookie: "tty",
          },
          {
            id:569732,
            cookie: "skll",
          },
        ],
      },

]);





//work restart 看這裡 reactive
// const filtered = ["K", "pp", "bay", "leon"];
// const objfilter = Object.entries(foodData);
//   const filteredData = objfilter.filter((it) => {  //跑左邊比對
//     for (let i = 0; i < filtered.length; i++) {
//       if (it[1].name.includes(filtered[i])) {  //陣列比對 跑右邊
//         console.log("123");
//         return it;  //回傳值
//       }
//     }
//   });
 
//   console.log("filtered", filteredData);

let AryAA = [2,4,6,8,10,12,14]

const comp = computed(() => {
console.log('in')

let res = ref(false)

const decad = AryAA.reduce((acc, cur)=>{
  if(cur > 10){
    acc.push(cur)
  }

  return acc
},[])
console.log(decad)

decad.length > 3 ? res.value = true : res.value = false
  


return res
})

setTimeout(()=>{
  AryAA = [2,10,14,16,22,13]
  
console.log('computed', comp.value)
  
},2000)

console.log('computed', comp.value)









//work restart 看這裡 (ref)
const filtered = ["K", "pp", "bay", "leon"];

const objfilter = Object.entries(foodData);


 console.log(foodData)
 console.log(objfilter)
// const filteredData = ref( objfilter.filter((it) => {  //跑左邊比對
//     for (let i = 0; i < filtered.length; i++) {
//       if (it[1].name.includes(filtered[i])) {  //陣列比對 跑右邊
//         console.log("123");
//         return it;  //回傳值
//       }
//     }

//   }));

 
  // console.log("filtered", filteredData);




// console.log('data', objfilterW);

// for(let i =0;i<objfilter.length;i++){
//   for(let j=0;j<=filtered.length;j++){
//     if(objfilterW[i][1].includes(filtered[j])){
//       deta.push(objfilterW[i][1])
//         console.log('for deta', deta)

//     }
//      console.log('i',i)

//   }
// }

// console.log('deta', deta);
let arrayA = ref(["1", "2", "3", "4", "5"])
let arrayB = ref(["5", "6", "7", "8", "9"])


console.log(foodData[0]);


const ttData = objfilter.reduce((acc, cur) => {

  return  acc.concat(cur)
},[])
console.log(ttData)

// let deta = reactive(foodData)
// console.log('default', deta)
let status = ref(0)
const changeTem = function () {
  //work restart
    foodData.value = filteredData.value;
//   // deta = reactive(filteredData)
//   // console.log('change', deta)
//   const filteredData = objfilter.filter((it) => {
//     for (let i = 0; i < filtered.length; i++) {
//       if (it[1].name.includes(filtered[i])) {
//         console.log("123");
//         return it;
//       }
//     }

//     // return it[1].name ==  filtered[index]
//   });
arrayA.value = arrayB.value
//   // for 迴圈  判斷  index 值 change
//   console.log("filtered", filteredData);
  // foodData = reactive(filteredData);

 console.log(foodData)

};

const txt = ref(0)





</script>

<template>
<Practice></Practice>
<section v-if='false'>
<p></p>
  <button @click="changeTem">123</button>
  <input type="text" v-model="txt">
  <h2>{{comp}}</h2>
  <h1>{{txt}}</h1>
  <h2 >sum = {{sum}}</h2>
  <h2>num = {{num}}</h2>
  <button @click="changeSum()">change Sum</button>
  <div class="star">
    <div class="row">
      <div class="col-3 p-3" v-for="(item, i) in foodData" :key="i">
        <div class="card">
          <img src="" class="card-img-top" alt="..." />
          <div class="card-body">
            <div class="r d-flex justify-content-around mb-3">
              <h5 class="card-title">Card title + {{ item }}</h5>
              <!-- <h3>{{ item.foodColumn[0].country }}</h3> -->
              <button @click="cancelStar(item)"></button>
            </div>

            <p class="card-text">
              Some quick example text to build on the card title and make up the
              bulk of the card's content.
            </p>
            <a href="#" class="btn btn-primary">Go somewhere</a>
          </div>
        </div>
      </div>
    </div>
  </div>
  <h2 class="mt-5">主單</h2>
  <div class="content mt-5 container">
    <div class="row mx-auto">
      <keep-alive>
      <div class="col-3 p-3" v-for="(item, i) in arrayA" :key="i">
        <div class="card">
          <img src="" class="card-img-top" alt="..." />
          <div class="card-body">
            <div class="r d-flex justify-content-around mb-3">
              <h5 class="card-title">Card title + {{ item }}</h5>
              <button @click="getStar(item)">{{ item.id }}</button>
            </div>

            <p class="card-text">
              Some quick example text to build on the card title and make up the
              bulk of the card's content.
            </p>
            <a href="#" class="btn btn-primary">Go somewhere</a>
          </div>
        </div>
      </div>
          </keep-alive>
    </div>
  </div>

  <!-- <div class="div">
    <h1 class="text-info">test 釘選</h1>
    <ul v-for="(item ,i)in arrayA" :key="i">
      <li>{{ item }}</li>
    </ul>
  </div> -->
  </section>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
