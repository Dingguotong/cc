<template>
  <div class="chengshi">
      <div class="dingwei">
        {{dingwei.name}}
      </div>
      <p>热门城市</p>
      <ul class="remen">
        <li class="di" v-for='(a,i) in remenlist' :key='i'>
          {{a.name}}
        </li>
      </ul>
      <!-- A -->
      <p>A</p>
      <ul class="diA">
          <li class="di" v-for='(a,i) in data.A' :key='i' @click='to(i)'>
              {{a.name}}
          </li>
      </ul>
      <!-- B -->
      <p>B</p>
      <ul class="diA">
          <li class="di" v-for='(a,i) in data.B' :key='i'>
          {{a.name}}
        </li>
      </ul>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'cheng',
  data() { 
    return {
      dingwei:[

      ],
      remenlist:[

      ],
      data:[

      ]
    }
  },
   created(){
    axios.get('http://elm.cangdu.org/v1/cities?type=guess').then((msg)=>{
      console.log(msg)
      this.dingwei=msg.data
    })
    axios.get('http://elm.cangdu.org/v1/cities?type=hot').then((msg)=>{
      console.log(msg)
      this.remenlist=msg.data
    })
    axios.get('http://elm.cangdu.org/v1/cities?type=group').then((msg)=>{
      console.log(msg)
      this.data=msg.data
    })
  },
  props: [

  ],
  components:{
  },
  mounted() {

  },
  methods:{
    to(n){
      this.$router.push({path:'/dizhi',query:{A:this.data.A[n].name}})
    }
  },
 }
</script>

<style lang="scss" scoped>
p{
  width: 100%;
  height: 0.3rem;
}
.chengshi{
  width: 100%;
  
  
  
}
.remen{
    width: 100%;
    height: 2rem;
    display: flex;
    flex-wrap: wrap;
    .di{
      width: 24%;
      height: 0.4rem;
      border: 1px solid #efefef;
      text-align: center;
      line-height: 0.4rem;
    }
  }
.diA{
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  .di{
      width: 24%;
      height: 0.4rem;
      border: 1px solid #efefef;
      text-align: center;
      line-height: 0.4rem;
    }
}

</style>