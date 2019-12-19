<template>
  <div class="test">
    <van-grid :border="false" :column-num="1">
      <img alt="Vue logo" src="../assets/timg.png" height="100" width="100%">
    </van-grid>
    <!-- 两端对齐 -->
    <van-tabs  sticky>

      <van-tab title="中国机长 " v-for="value in 6"
               :key="value"
               icon="photo-o"
               text="文字"
      >
        <van-list
          v-model="loading"
          :finished="finished"
          finished-text="没有更多了"
          @load="onLoad"
        >
          <van-cell
            v-for="item in list"
            :key="item"
            :title="item"
          />
        </van-list>
      </van-tab>
    </van-tabs>
  </div>
</template>
<script>
export default {
  name: 'test',
  props: {
    msg: String
  },
  data () {
    return {
      list: [],
      loading: false,
      finished: false
    }
  },
  methods: {
    onLoad () {
      // 异步更新数据
      setTimeout(() => {
        for (let i = 0; i < 10; i++) {
          this.list.push(this.list.length + 1)
        }
        // 加载状态结束
        this.loading = false
        console.log('loading...' + this.list.length)

        // 数据全部加载完成
        if (this.list.length >= 100) {
          this.finished = true
        }
      }, 500)
    }
  }
}
</script>
<style scoped lang="scss">
</style>
