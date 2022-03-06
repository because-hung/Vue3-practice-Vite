<script setup>
import { computed, onUpdated, reactive, ref, watch } from "vue";

defineProps({
  msg: String,
});

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

const getStar = function (item) {
  console.log(filterData);

  const found = filterData.find((el) => {
    return el.id === item.id;
  });

  if (!found) {
    filterData.push(item);
    localStorage.setItem("NumData", JSON.stringify(filterData));
  }

  console.log(filterData);
};
const cancelStar = function (item) {
  const found = filterData.find((el) => {
    return el.id === item.id;
  });

  if (found) {
    filterData.splice(0, 1);
    localStorage.setItem("NumData", JSON.stringify(filterData));
  }

  console.log(filterData);
};

//work obj array

let foodData = reactive([
  {
    name: "tom17",
    foodColumn: [
      {
        country: "USA",
        id: "01",
        food: [
          {
            cookie: "straw",
          },
        ],
      },
    ],
  },
  {
    name: "bay12",
    foodColumn: [
      {
        country: "CANA",
        id: "02",
        food: [
          {
            cookie: "straw",
          },
        ],
      },
    ],
  },
  {
    name: "Kom",
    foodColumn: [
      {
        country: "lorea",
        id: "03",
        food: [
          {
            cookie: "straw",
          },
        ],
      },
    ],
  },
  {
    name: "pp",
    foodColumn: [
      {
        country: "USAaaa",
        id: "04",
        food: [
          {
            cookie: "straw",
          },
        ],
      },
    ],
  },
]);

//work restart 看這裡
const filtered = ["K", "pp", "bay", "leon"];

const objfilter = Object.entries(foodData);


  const filteredData = objfilter.filter((it) => {  //跑左邊比對
    for (let i = 0; i < filtered.length; i++) {
      if (it[1].name.includes(filtered[i])) {  //陣列比對 跑右邊
        console.log("123");
        return it;  //回傳值
      }
    }

  });

 
  console.log("filtered", filteredData);




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

console.log(foodData);
// let deta = reactive(foodData)
// console.log('default', deta)
let status = ref(0)
const changeTem = function () {
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

//   // for 迴圈  判斷  index 值 change
//   console.log("filtered", filteredData);
//   // foodData = reactive(filteredData);
status.value = 1

};
 console.log(status)

let arrayA = reactive(["1", "2", "3", "4", "5"])
let arrayB = reactive(["5", "6", "7", "8", "9"])





</script>

<template>
  <button @click="changeTem">123</button>

  <div class="star">
    <div class="row">
      <div class="col-3 p-3" v-for="(item, i) in arrayA" :key="i">
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
      <div class="col-3 p-3" v-for="(item, i) in data" :key="i">
        <div class="card">
          <img src="" class="card-img-top" alt="..." />
          <div class="card-body">
            <div class="r d-flex justify-content-around mb-3">
              <h5 class="card-title">Card title + {{ item.user }}</h5>
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
    </div>
  </div>

  <!-- <div class="div">
    <h1 class="text-info">test 釘選</h1>
    <ul v-for="(item ,i)in arrayA" :key="i">
      <li>{{ item }}</li>
    </ul>
  </div> -->
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
