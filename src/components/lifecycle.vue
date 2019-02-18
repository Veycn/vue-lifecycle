<template>
  <div>{{a}}</div>
</template>

<script>
export default {
  name: 'lifecycle',
  data () {
    return {
      a: 12
    }
  },
  methods: {
    b () {
      console.log('i am methods b')
    }
  },
  beforeCreate () {
    console.log('---------------------')
    console.log('beforeCreate...')
    if (!this.b) {
      console.log('此时 methods 还不存在')
    }
    if (!this.a) {
      console.log('此时 data 还不存在')
    }
    console.log('---------------------')
  },
  created () {
    console.log('created...')
    console.log('a = ' + this.a)
    this.b()
    console.log('data, methods 都已存在且可使用')
    console.log('---------------------')
  },
  beforeMount () {
    console.log('beforeMount...')
    console.log('此时去寻找 el 或者 vm.$mount()')
    console.log('vue 实例已经找到要挂在的dom')
    console.log('寻找 template')
    console.log('template 不存在, 编译 el.outerHTML 作为 template')
    console.log('此时, template即使不存在, 也存在了')
    console.log('template 存在, 将其编译进 render 函数')
    console.log('AST, VNode 在此形成')
    console.log('得到了真实的 dom')
    console.log('----------------------')
  },
  mounted () {
    console.log('mounted...')
    console.log('此时真实 dom 已经挂载完毕')
    console.log('----------------------')
    this.a = 20
  },
  beforeUpdate () {
    console.log('beforeUpdate...')
    console.log('更新前的数据比对操作')
    console.log('执行更新...')
    console.log('----------------------')
  },
  updated () {
    console.log('updated...')
    console.log('组件更新已完成')
    console.log('----------------------')
  },
  beforeDestroy () {
    console.log('beforeDestroy...')
    console.log('销毁前的准备工作')
    console.log('取消监听器, 移除子组件等')
    console.log('执行销毁...')
    console.log('----------------------')
  },
  destroyed () {
    console.log('destroyed...')
    console.log('组件已销毁')
    console.log('lifecycle end')
  }
}
</script>

<style scoped>

</style>
