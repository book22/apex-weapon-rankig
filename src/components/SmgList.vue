<template>
  <div>
    <h3>サブマシンガン</h3>
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
          <tr v-for="submachinegun in Sortedsubmachineguns" :key="submachinegun.no">
            <td>{{ submachinegun.like }}</td>
            <td><img :src='submachinegun.img' width="80px"></td>
            <td>{{ submachinegun.name }}</td>
            <td class="pc-width">{{ submachinegun.damage }}</td>
            <td class="pc-width">{{ submachinegun.dps }}</td>
            <td class="pc-width">{{ submachinegun.rate }}</td>
            <td class="pc-width"><img :src='submachinegun.kind' width="40px"></td>
            <button class="vote" :disabled="isPush" @click="submachinegun.like ++; isPush = true;">投票</button>
          </tr>
        </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data(){
    return{
      submachineguns: [
        { 
          no:1,
          like: 0 ,
          img:require('@/assets/images/submachinegun/a.png'),  
          name:'プラウラー'    ,
          damage:'15(23)',
          dps:'122',
          rate:'20',
          kind:require('@/assets/images/ammo/heavy.png')
          },
        { 
          no:2,
          like: 0 ,
          img:require('@/assets/images/submachinegun/b.png'),
          name:'R99',
          damage:'11(17)',
          dps:'216',
          rate:'18',
          kind:require('@/assets/images/ammo/light.png')
          },
        { 
          no:3,
          like: 0 ,
          img:require('@/assets/images/submachinegun/c.png'),   
          name:'オルタネーター',      
          damage:'15(22)',
          dps:'150',
          rate:'10',
          kind:require('@/assets/images/ammo/light.png')
          },
        { 
          no:4,
          like: 0,
          img:require('@/assets/images/submachinegun/d.png'), 
          name:'ボルト',  
          damage:'16(24)',
          dps:'192',
          rate:'12',
          kind:require('@/assets/images/ammo/energy.png')
          }
      ],
      isPush: false,
    }
  },
  computed: {
    Sortedsubmachineguns(){
      return this.submachineguns.slice().sort((a, b) => {
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
    background-color: rgb(233, 236, 182);
}
</style>