<template>
  <div>
    <h3>ライトマシンガン</h3>
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
          <tr v-for="lightmachinegun in Sortedlightmachineguns" :key="lightmachinegun.no">
            <td>{{ lightmachinegun.like }}</td>
            <td><img :src='lightmachinegun.img' width="80px"></td>
            <td>{{ lightmachinegun.name }}</td>
            <td class="pc-width">{{ lightmachinegun.damage }}</td>
            <td class="pc-width">{{ lightmachinegun.dps }}</td>
            <td class="pc-width">{{ lightmachinegun.rate }}</td>
            <td class="pc-width"><img :src='lightmachinegun.kind' width="40px"></td>
            <button class="vote" :disabled="isPush" @click="lightmachinegun.like ++; isPush = true;">投票</button>
          </tr>
        </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data(){
    return{
      lightmachineguns: [
        { 
          no:1,
          like: 0 ,
          img:require('@/assets/images/lightmachinegun/a.png'),  
          name:'スピットファイア'    ,
          damage:'18(36)',
          dps:'162',
          rate:'9',
          kind:require('@/assets/images/ammo/heavy.png')
          },
        { 
          no:2,
          like: 0 ,
          img:require('@/assets/images/lightmachinegun/b.png'),
          name:'ディヴォーション',
          damage:'17(34)',
          dps:'255',
          rate:'15',
          kind:require('@/assets/images/ammo/energy.png')
          },
        { 
          no:3,
          like: 0 ,
          img:require('@/assets/images/lightmachinegun/c.png'),   
          name:'Lスター',      
          damage:'18(36)',
          dps:'180',
          rate:'10',
          kind:require('@/assets/images/ammo/energy.png')
          }
      ],
      isPush: false,
    }
  },
  computed: {
    Sortedlightmachineguns(){
      return this.lightmachineguns.slice().sort((a, b) => {
      if(a.like > b.like) return -1
      if(a.like < b.like) return 1
      return 0
      });
    }
}
}
</script>

<style scoped>
h3{
    background-color: rgb(230, 186, 247);
}
</style>