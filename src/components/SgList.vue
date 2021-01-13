<template>
  <div>
    <h3>ショットガン</h3>
    <table>
      <thead>
      <tr>
      <!-- <th>No</th> -->
      <th>投票数</th>
      <th>画像</th>
      <th>武器</th>
      <th class="pc-width">胴（頭）</th>
      <th class="pc-width">DPS</th>
      <th class="pc-width">連射速度</th>
      <th class="pc-width">種類</th>
      </tr>
      </thead>
        <tbody>
          <tr v-for="shotgun in Sortedshotguns" :key="shotgun.no">
            <td>{{ shotgun.like }}</td>
            <td><img :src='shotgun.img' width="80px"></td>
            <td>{{ shotgun.name }}</td>
            <td class="pc-width">{{ shotgun.damage }}</td>
            <td class="pc-width">{{ shotgun.dps }}</td>
            <td class="pc-width">{{ shotgun.rate }}</td>
            <td class="pc-width"><img :src='shotgun.kind' width="40px"></td>
            <button class="vote" :disabled="isPush" @click="shotgun.like ++; isPush = true;">投票</button>
          </tr>
        </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data(){
    return{
      shotguns: [
        { 
          no:1,
          like: 0 ,
          img:require('@/assets/images/shotgun/a.png'),  
          name:'モザンビーク',
          damage:'15(22)',
          dps:'99',
          rate:'2.2',
          kind:require('@/assets/images/ammo/shotgun.png')
          },
        { 
          no:2,
          like: 0 ,
          img:require('@/assets/images/shotgun/b.png'),
          name:'マスティフ',
          damage:'104(128)',
          dps:'104',
          rate:'1.3',
          kind:require('@/assets/images/ammo/shotgun.png')
          },
        { 
          no:3,
          like: 0 ,
          img:require('@/assets/images/shotgun/c.png'),   
          name:'ピースキーパー',      
          damage:'110(143)',
          dps:'81',
          rate:'0.97',
          kind:require('@/assets/images/ammo/shotgun.png')
          },
        { 
          no:4,
          like: 0,
          img:require('@/assets/images/shotgun/d.png'), 
          name:'EVA-8',  
          damage:'63(90)',
          dps:'126',
          rate:'2',
          kind:require('@/assets/images/ammo/shotgun.png')
          }
      ],
      isPush: false,
    }
  },
  computed: {
    Sortedshotguns(){
      return this.shotguns.slice().sort((a, b) => {
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
    background-color: rgb(247, 186, 186);
}
</style>
