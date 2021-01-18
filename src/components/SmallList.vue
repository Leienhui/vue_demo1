<template>
  <div>
    <small-bar v-for="(item,index) in arr" :key="index" :content="item" @modifyContent="modifyContentHandler($event,index)" @del="delHander(index)"  @down="$emit('down',index)" @up="$emit('up',index)"/>
        <button @click="$emit('new-content')">添加新项</button>
  </div>
</template>

<script>
import SmallBar from './SmallBar.vue'
export default {
  data () {
    return {
    }
  },
  components: { SmallBar },
  props: ['arr'],
  methods: {
    modifyContentHandler (content, index) {
      this.$emit('modifyContent', {content, index})
    },
    delHander (index) {
      this.$emit('delHander', index)
    }
  }
}
</script>

<style lang="less" scoped>

</style>
