<template>
  <div>
    <p>{{langKey('不可用按钮')}}</p>
        <yo-button>{{langKey('不可用按钮')}}</yo-button>
        <yo-button disabled>{{langKey('不可用按钮')}}(disabled)</yo-button>
  </div>
</template>
<script>
export default {
  data() {
    return {

    };
  },
  mounted() {
	  this.$emit('loaded')
  },
};
</script>

<style lang="less" scoped>
  .yo-btn{
    margin-bottom: 10px;    
  }
</style>
