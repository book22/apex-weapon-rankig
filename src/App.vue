<template>
<div>
  <ApexHeader></ApexHeader>
  <AsList></AsList>
  <SmgList></SmgList>
  <LmgList></LmgList>
  <SniperrifleList></SniperrifleList>
  <ShotgunList></ShotgunList>
  <PistolList></PistolList>
</div>
</template>

<script>
 import ApexHeader from "./components/ApexHeader.vue";
 import AsList from "./components/AsList.vue";
 import SmgList from "./components/SmgList.vue";
 import LmgList from './components/LmgList.vue';
 import SniperrifleList from './components/SrList.vue';
 import ShotgunList from './components/SgList.vue';
 import PistolList from './components/PList.vue';
 


  export default {
    data(){
      return{
      };
    },
    components: {
      ApexHeader,
      AsList,
      SmgList,
      LmgList,
      SniperrifleList,
      ShotgunList,
      PistolList
    }
  }
</script>
