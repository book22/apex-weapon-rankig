<template>
  <div>
    <h3>スナイパーライフル</h3>
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
          <tr v-for="sniperrifle in Sortedsniperrifles" :key="sniperrifle.no">
            <td>{{ sniperrifle.like }}</td>
            <td><img :src='sniperrifle.img' width="80px"></td>
            <td>{{ sniperrifle.name }}</td>
            <td class="pc-width">{{ sniperrifle.damage }}</td>
            <td class="pc-width">{{ sniperrifle.dps }}</td>
            <td class="pc-width">{{ sniperrifle.rate }}</td>
            <td class="pc-width"><img :src='sniperrifle.kind' width="40px"></td>
            <button class="vote" :disabled="isPush" @click="sniperrifle.like ++; isPush = true;">投票</button>
          </tr>
        </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data(){
    return{
      sniperrifles: [
        { 
          no:1,
          like: 0 ,
          img:require('@/assets/images/sniperrifle/a.png'),  
          name:'クレーバー',
          damage:'145(197)',
          dps:'145',
          rate:'0.47',
          kind:require('@/assets/images/ammo/sniper.png')
          },
        { 
          no:2,
          like: 0 ,
          img:require('@/assets/images/sniperrifle/b.png'),
          name:'トリプルテイク',
          damage:'23(46)',
          dps:'86',
          rate:'1.25',
          kind:require('@/assets/images/ammo/sniper.png')
          },
        { 
          no:3,
          like: 0 ,
          img:require('@/assets/images/sniperrifle/c.png'),   
          name:'ロングボウ',      
          damage:'55(115)',
          dps:'71',
          rate:'1.3',
          kind:require('@/assets/images/ammo/sniper.png')
          },
        { 
          no:4,
          like: 0,
          img:require('@/assets/images/sniperrifle/d.png'), 
          name:'チャージライフル',  
          damage:'45(56)',
          dps:'31.5',
          rate:'0.7',
          kind:require('@/assets/images/ammo/sniper.png')
          },
        { 
          no:5,
          like: 0 ,
          img:require('@/assets/images/sniperrifle/e.png'),   
          name:'センチネル',    
          damage:'70(130)',
          dps:'36',
          rate:'0.55',
          kind:require('@/assets/images/ammo/sniper.png')
          },
      ],
      isPush: false,
    }
  },
  computed: {
    Sortedsniperrifles(){
      return this.sniperrifles.slice().sort((a, b) => {
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
     background-color: rgb(186, 187, 247);
 }
</style>
