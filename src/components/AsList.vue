<template>
  <div>
    <h3>アサルトライフル</h3>
    <div>
    <table>
      <thead>
      <tr>
      <th>票数</th>
      <th>画像</th>
      <th>武器</th>
      <th class="pc-width">胴（頭）</th>
      <th class="pc-width">DPS</th>
      <th class="pc-width">連射速度</th>
      <th class="pc-width">種類</th>
      </tr>
      </thead>
        <tbody>
          <tr v-for="assaultrifle in SortedAssaultrifles" :key="assaultrifle.name">
            <td>{{ assaultrifle.like}}</td>
            <td><img :src='assaultrifle.img' width="80px"></td>
            <td>{{ assaultrifle.name }}</td>
            <td class="pc-width">{{ assaultrifle.damage }}</td>
            <td class="pc-width">{{ assaultrifle.dps }}</td>
            <td class="pc-width">{{ assaultrifle.rate }}</td>
            <td class="pc-width"><img :src='assaultrifle.kind' width="40px"></td>
            <button class="vote" :disabled="isPush" @click="votePush(assaultrifle)">投票</button>
          </tr>
        </tbody>
    </table>
    </div>
  </div>
</template>

<script>
// import axios from "axios";
export default {
  data(){
    return{
      assaultrifles: [
        { 
          no:1,
          like: 0,
          img:require('@/assets/images/assaultrifle/hemlok.png'),  
          name:'ヘムロック'    ,
          damage:'22(38.5)',
          dps:'132',
          rate:'15',
          kind:require('@/assets/images/ammo/heavy.png')
          },
        { 
          no:2,
          like: 0,
          img:require('@/assets/images/assaultrifle/flatline.png'),
          name:'フラットライン',
          damage:'19(38)',
          dps:'190',
          rate:'10',
          kind:require('@/assets/images/ammo/heavy.png')
          },
        { 
          no:3,
          like: 0 ,
          img:require('@/assets/images/assaultrifle/havoc.png'),   
          name:'ハボック',      
          damage:'18(36)',
          dps:'201',
          rate:'11.2',
          kind:require('@/assets/images/ammo/energy.png')
          },
        { 
          no:4,
          like: 0,
          img:require('@/assets/images/assaultrifle/carbine.png'), 
          name:'R301カービン',  
          damage:'14(28)',
          dps:'189',
          rate:'13.5',
          kind:require('@/assets/images/ammo/light.png')
          },
        { 
          no:5,
          like: 0 ,
          img:require('@/assets/images/assaultrifle/scout.png'),   
          name:'G7スカウト',    
          damage:'34(68)',
          dps:'153',
          rate:'4.0',
          kind:require('@/assets/images/ammo/light.png')
          },
      ],
      isPush: false,
      likes: []
    }
  },
  // created(){
  //   axios.get(
  //     'https://firestore.googleapis.com/v1/projects/apex-weapon-app/databases/(default)/documents/likes'
  //   ).then(res => {
  //     this.assaultrifles.like = res.data.documents.fields
  //     console.log(res)
  //   });
  // },
  computed: {
    SortedAssaultrifles(){
      return this.assaultrifles.slice().sort((a, b) => {
      if(a.like > b.like) return -1
      if(a.like < b.like) return 1
      return 0
      });
    }
},
  methods: {
    votePush(assaultrifle) {
      assaultrifle.like ++;
      this.isPush = true;
      // axios.post('https://firestore.googleapis.com/v1/projects/apex-weapon-app/databases/(default)/documents/likes',
      // {
      //   fields: {
      //     stringValue: assaultrifle.name,
      //     integerValue : assaultrifle.like
      //   }
      // }
      // );
    }
  }
}
</script>

<style scoped>
h3{
    background-color: rgb(186, 220, 247);
}
</style>
