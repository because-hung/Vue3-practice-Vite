<script setup>
import { reactive, ref } from "vue";

defineProps({
  msg: String,
});

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
const filterData = reactive([]);
const getStar = function (item) {
 if(!filterData.includes(item)){
   filterData.push(item)
 }
 console.log(filterData)
};
const cancelStar = function(item){
if(filterData.includes(item)){
   filterData.splice(0,1)
 }
 console.log(filterData)
};

</script>

<template>
  <h1 class="text-info">test 釘選</h1>
  <div class="star">
    <div class="row">
      <div class="col-3 p-3" v-for="(item, i) in filterData" :key="i">
        <div class="card">
          <img src="" class="card-img-top" alt="..." />
          <div class="card-body">
            <div class="r d-flex justify-content-around mb-3">
              <h5 class="card-title">Card title + {{ item.user }}</h5>
              <button @click="cancelStar(item)">{{ item.id }}</button>
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
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
