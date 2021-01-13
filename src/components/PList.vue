<template>
  <div>
    <h3>ピストル</h3>
    <table>
      <thead>
      <tr>
      <!-- <th>No</th> -->
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
          <tr v-for="pistol in Sortedpistols" :key="pistol.no">
            <td>{{ pistol.like }}</td>
            <td><img :src='pistol.img' width="80px"></td>
            <td>{{ pistol.name }}</td>
            <td class="pc-width">{{ pistol.damage }}</td>
            <td class="pc-width">{{ pistol.dps }}</td>
            <td class="pc-width">{{ pistol.rate }}</td>
            <td class="pc-width"><img :src='pistol.kind' width="40px"></td>
            <button class="vote" :disabled="isPush" @click="pistol.like ++; isPush = true;">投票</button>
          </tr>
        </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data(){
    return{
      pistols: [
        { 
          no:1,
          like: 0 ,
          img:require('@/assets/images/pistol/a.png'),  
          name:'ウィングマン',
          damage:'45(90)',
          dps:'117',
          rate:'2.6',
          kind:require('@/assets/images/ammo/heavy.png')
          },
        { 
          no:2,
          like: 0 ,
          img:require('@/assets/images/pistol/b.png'),
          name:'RE45',
          damage:'12(16)',
          dps:'143',
          rate:'13',
          kind:require('@/assets/images/ammo/light.png')
          },
        { 
          no:3,
          like: 0,
          img:require('@/assets/images/pistol/c.png'),   
          name:'P2020',      
          damage:'15(19)',
          dps:'110',
          rate:'8.5',
          kind:require('@/assets/images/ammo/light.png')
          }
      ],
      isPush: false,
    }
  },
  computed: {
    Sortedpistols(){
      return this.pistols.slice().sort((a, b) => {
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
    background-color: rgb(203, 247, 186);
}
</style>