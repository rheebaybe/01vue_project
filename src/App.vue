<template>
<my-banner/>

<!-- <div class="black-bg" v-if="proView == true">
  <div class="white-bg">
    <img v-bind:src="product[proNum].image">
    <div>{{product[proNum].title}}</div>
    <div>{{product[proNum].price}}</div>
    <div>{{product[proNum].content}}</div>
    <button v-on:click="proView=false">닫기</button>
  </div>
</div> -->
<modal :product="product" :proView="proView" :proNum="proNum"
@modalClose="proView=false" />
<!-- v-bind:작명="아래데이터값" -->


<!-- <ul class="view">
  <li v-for="(item,i) in product" :key="i">
    <img v-bind:src="product[i].image">
    <div>{{product[i].title}}
      <div><span v-on:click="proView=true;proNum=i">[상세보기]</span></div>
    </div>
    <div>{{product[i].price}}</div>
  </li>
</ul> -->


<product v-bind:product="product[i]" v-for="(item,i) in product" v-bind:key="i" 
@modalOpen="proView=true;proNum=$event" />
<!-- 0번자리가 5번 돌아갈수있게 fot-in문을 써준다
$event는 'modalOpen'뒤에 product.id를 가져온것이다 -->

</template>
// html소스 넣는곳

<script>
import vdata from './data.js'
import banner from './components/banner.vue'
import modal from './components/modal.vue'
import product from './components/product.vue'

export default {
  name: 'App',
  data(){
    return{
      proNum:0,
      proView:false,
      product: vdata,
    }
  },
  components:{
    'my-banner':banner,
     modal:modal,
     product:product,
  }
}
</script>

<style>
html,body{
  height: 100%;
}
*{
  margin:0 auto;
  padding:0;
}
li{
  list-style: none;
}
img{
  width: 100%;
}
.view li{
  margin-bottom: 20px;
}
.black-bg{
  position: fixed;
  top:0;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
}
.white-bg{
  width:80%;
  background: #fff;
  border-radius: 5px;
  padding:20px;
}
</style>
