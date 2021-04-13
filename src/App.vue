<template>
  <div class="container">
      
      <div class="z" :style="{'margin-left':'-'+('108' * activeIndex) + '%'}">
          <li 
              v-for="(item,idx) in arr"
              :key="idx">
              <img  :src="item.src">
          </li>
      </div>
      
      
      <li class="btnsSlides"
          v-for="(item,idx) in arr"
          :key="idx">
          <button :class="{active:activeIndex === idx,btnSlide:activeIndex!=idx}" @click="setIdx(idx)">
          slide {{idx+1}}
          </button>
      </li>
      <button class="btnNext" @click="next">NEXT</button>
      <button class="btnPrev" @click="prev">PREV</button>

  </div>
</template>

<script>export default {
  name: 'App',
  data(){
    return{
      activeIndex:0,
      arr:[
          {name:'1',src:'1.jpg'},
          {name:'2',src:'2.jpg'},
          {name:'3',src:'3.jpg'},
          {name:'3',src:'4.jpg'},
          {name:'3',src:'5.jpg'}
      ]
    }
  },
  methods:{
    prev(){
      if (this.activeIndex > 0) {
          this.activeIndex--
      }else{
        this.activeIndex=4
      }
    },
    next(){
      if (this.activeIndex<4) {
          this.activeIndex++
      }else{
        this.activeIndex=0
      }
      
      
    },
    setIdx(id){
        this.activeIndex=id
        console.log(id);

    }
  },
  computed:{
    curentSlide(){
        return this.arr[this.activeIndex].src
    }
  }
}
</script>

<style>
li {
    list-style-type: none; 
   }
.z{
  display: flex;
  transition: all ease .5s;
}
.btnsSlides{
  margin-left: 25px;
}
.container{
  overflow: hidden;
  max-width: 595px;
  margin: 100px auto;
}
.btnPrev{
  width: 70px;
  height: 30px;
  background-color: rgb(246, 156, 114);
  border: 2px solid black;
  color: black;
  outline: none;
  border-radius: 20px;
  position: absolute;
  bottom: 150px;
  left: 830px
}
.btnPrev:hover{
   background-color: rgb(243, 83, 55);
  border: 2px solid black;
  font-size: 15px;
  font-size: 15px;
}
.btnNext{
  width: 70px;
  height: 30px;
  background-color: rgb(226, 228, 95);
  border: 2px solid black;
  color: black;
  outline: none;
  border-radius: 20px;
  position: absolute;
  right: 830px;
  bottom: 150px;
}
.btnNext:hover{
  background-color: rgb(251, 255, 26);
  border: 3px solid black;
  font-size: 15px;
}
.btnSlide{
  height: 80px;
  width: 100px;
  font-size: 15px;
  float: left;
  margin: 5px;
  border-radius: 15px;
  outline: 0;
  background-color: rgb(216, 233, 199);
  cursor: pointer;
  
}
.btnSlide:hover{
  background-color: rgb(200, 250, 150);
  font-weight: 600;
  cursor: pointer;
}
.active{
  height: 80px;
  width: 100px;
  float: left;
  margin: 5px;
  outline: 0;
  font-weight: 600;
  font-size: 15px;
  border-radius: 15px;
  border: 5px solid rgb(181, 197, 35);
  background-color: rgb(146, 240, 70);
}
body{
  background-color: rgb(28, 28, 66);
}
</style>

