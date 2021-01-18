<template>
  <div>
    <span v-if="nowState==0" class="span" @dblclick="nowState=1 ">{{content}} </span>
    <input type="text" v-if="nowState==1" class="input"   @blur="nowState=0;  $emit('modifyContent',$event.target.value)">
    <button @click="$emit('del')">删除</button>
    <button @click="$emit('down')">👇</button>
    <button @click="$emit('up')">👆</button>

  </div>
</template>

<script>
export default {
  props: ['content'],
  data () {
    return {
      nowState: 0

    }
  }

}
</script>

<style lang="less" scoped>
.span{
  width: 300px;
  display: block;
  float: left;

}
.input{
  width: 292px;
  display: block;
  float: left;

}

</style>
