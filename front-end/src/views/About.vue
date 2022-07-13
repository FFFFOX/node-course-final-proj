<template>
<div id="About">
  <div class="aboutHomeTop">
    <h3>🤖关于我们</h3>
    <p class="mt-2">自由创作 · 随心而动</p>
  </div>
  <div class="text-center my-2">
    <p>sadjlasdjl</p>
  </div>
  <div class="aboutHomeMiddle">
    <div class="title">专栏 · 发现</div>

  </div>
</div>
</template>

<script lang="ts">
import { defineComponent, onMounted } from 'vue'
import { useStore } from 'vuex'
import { useRouter } from 'vue-router'

export default defineComponent({
  name: 'Column',
  setup () {
    const store = useStore()
    const router = useRouter()
    onMounted(() => {
      store.dispatch('asyncGetColumn')
    })
    const navigateTo = (path: string): void => {
      router.push(path)
    }
    return {
      navigateTo
    }
  }
})
</script>

<style>
#aboutHome {
  width: 100%;
}
.aboutHomeTop {
  height: 100px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding-top: 80px;
  margin: 2em 0;
  /* background: url('https://img.ffffox.space/0A183AF5-1B7A-4EEC-A600-3A73095A00EF_1_105_c.jpeg') no-repeat 100% 100%; */
}
.columnHomeMiddle {
  width: 70em;
  margin: 1em auto;
}
.aboutHomeMiddle > .title {
  font-weight: 600;
  text-align: center;
  margin-bottom: .3em;
}
</style>
