<template>
  <div>
    <small-list :arr="arr" @modifyContent="modifyContentFun($event)" @delHander="delHanderFun($event)" @down="downHanderFun($event)" @up="upHanderFun($event)" @new-content="newContent"/>
  </div>
</template>

<script>
import SmallList from './components/SmallList.vue'
export default {
  data () {
    return {
      arr: ['压力', '苹果', '上海的', '是你']
    }
  },
  components: {
    SmallList

  },
  methods: {
    modifyContentFun ({ content, index }) {
      console.log(content)
      console.log(index)
      // this.arr.splice(index, 1, content)
      this.arr = this.arr.map((item, _index) => (_index === index) && (content !== '') ? content : item)
    },
    delHanderFun (index) {
      this.arr = this.arr.filter((item, _index) => {
        if (_index !== index) {
          return item
        }
      })
    },
    downHanderFun (index) {
      if (index !== this.arr.length - 1) {
        let nowdata = this.arr.splice(index, 1)
        this.arr.splice(index + 1, 0, ...nowdata)
      }
    },
    upHanderFun (index) {
      if (index !== 0) {
        let nowdata = this.arr.splice(index, 1)
        this.arr.splice(index - 1, 0, ...nowdata)
      }
    },
    newContent () {
      this.arr.push('请输入添加数据')
    }
  }
}
</script>

<style lang="less" scoped>

</style>
