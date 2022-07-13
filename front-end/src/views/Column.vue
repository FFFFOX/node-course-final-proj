<template>
<div id="columnHome">
  <div class="columnHomeTop">
    <h3>🤖专栏</h3>
    <p class="mt-2">自由创作 · 随心而动</p>
  </div>
  <div class="text-center my-2">
    <button
      class="btn btn-outline-primary"
      @click.prevent="navigateTo('/post/create')"
    >
      开始写文章
    </button>
  </div>
  <div class="columnHomeMiddle">
    <div class="title">专栏 · 发现</div>
    <column-list :list="columnlist" />
  </div>
</div>
</template>

<script lang="ts">
import { computed, defineComponent, onMounted } from 'vue'
import ColumnList from '@/components/ColumnList.vue'
import { useStore } from 'vuex'
import { useRouter } from 'vue-router'

export default defineComponent({
  name: 'Column',
  components: { ColumnList },
  setup () {
    const store = useStore()
    const router = useRouter()
    onMounted(() => {
      store.dispatch('asyncGetColumn')
    })
    const columnlist = computed(() => store.state.columnList)
    const navigateTo = (path: string): void => {
      router.push(path)
    }
    return {
      columnlist,
      navigateTo
    }
  }
})
</script>

<style>
#columnHome {
  width: 100%;
}
.columnHomeTop {
  height: 300px;
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
.columnHomeMiddle > .title {
  font-weight: 600;
  text-align: center;
  margin-bottom: .3em;
}
</style>
