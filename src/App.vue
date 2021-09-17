<script setup>
import { ref, computed } from 'vue'
import Triangle from './Triangle.vue'
const S = ref(3)
const trianglesArray = computed(()=>{
  let triangles = [];
  for	(let i=1; i <= S.value; i++){
    let row = [];
    for(let j=1; j <= 2*i-1; j++){
      row.push(`(${i},${j})`);
    }
    triangles.push(row);
  }
  return triangles;
})
function shouldRotate(index){
  return index % 2 == 0;
}
</script>

<template>
  <label>S: <input type="number" style="width: 2em;" v-model="S"></label>	
  <div class="triangle-container">
    <div v-for="(row, indexRow) in trianglesArray">
      <Triangle v-for="(col, indexCol) in row" :x="indexRow" :y="indexCol" class="triangle" :rotate="indexCol % 2 == 1"></Triangle>
    </div>
  </div>
</template>
<style>
  .triangle-container{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  .triangle{
    margin-left: -50px;
    margin-top: -5px;
  }
</style>