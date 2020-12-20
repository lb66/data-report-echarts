<template>
  <div class="home">
    <top-view/>
    <sales-view/>
    <bottom-view/>
    <map-view/>
  </div>
</template>

<script>
import TopView from '../components/TopView.vue';
import MapView from '../components/MapView.vue'
import BottomView from '../components/BottomView.vue';
import SalesView from '../components/SalesView.vue';

export default {
  components: { TopView, BottomView, SalesView,MapView },
  name: 'Home'
}
</script>

<style >
.home{
  width: 100%;
  height: 100%;
  padding: 20px;
  background: #eee;
  box-sizing: border-box;
}
</style>


