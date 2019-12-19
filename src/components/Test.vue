<template>
  <div class="test">
    <!-- 两端对齐 -->
    <van-tabs v-model="active" sticky>

      <van-tab title="中国机长 "  v-for="value in 6"
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
  name: 'Test',
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
