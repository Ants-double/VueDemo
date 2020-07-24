<template>
  <div>
    Home
    <p v-if="msgJsonApp.msgFlog">{{msgJsonApp.msg}}</p>
    <h2>{{msg}}</h2>
  </div>
</template>

<script>
export default {
   props: ['msgJsonApp', 'author'],
  name: "Home",
 
  data: function() {
    return {
      msg: "Index page"
    };
  },
  methods: {
     getParams () {
        // 取到路由带过来的参数 
        let routerParams = this.$route.params.dataobj
        // 将数据放在当前组件的数据内
        this.msgJsonApp = routerParams
      }
  },
  watch: {
    // 监测路由变化,只要变化了就调用获取路由参数方法将数据存储本组件即可
      '$router': 'getParams'
  },
};
</script>
