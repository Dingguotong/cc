<template>
  <div class="dizhi">
      
      <div>
        <router-link to='/'>
        返回
        </router-link>
      </div>
      <div>{{msg}}</div>

      <div>
        <router-link to='/'>
        选择城市
        </router-link>
      </div>
  </div>
</template>

<script>
export default {
  name: 'dizhi',
  data() { 
    return {
        msg:""
    }
  },
  props: [

  ],
  components:{
  },
  mounted() {
      this.msg=this.$route.query.A
  },
  methods:{

  },
 }
</script>

<style lang="scss" scoped>
.dizhi{
    width: 100%;
    height: 300px;
    display: flex;
    justify-content: space-between;
}

</style>