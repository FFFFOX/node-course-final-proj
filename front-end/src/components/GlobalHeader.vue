<template>
<header>
  <nav class="navbar">
    <div class="column-center">
      <div class="text-logo">🤖</div>
      <ul class="nav column-center">
        <li v-for="({name, path, child}, i) in navList"
          :key="name"
          :class="{
            'c-item': true,
            'column-center': child,
            'nav-active': cIndex === i
          }"
          @click="handleNavbar(i)"
        >
          <router-link :to="path" v-if="!child">
            {{name}}
          </router-link>
          <!-- <dropdown title="专栏" tag="div" v-else>
            <dropdown-item v-for="c in child" :key="c.name">
              <router-link class="dropdown-item" :to="c.cpath">
                {{c.name}}
              </router-link>
            </dropdown-item>
          </dropdown> -->
        </li>
      </ul>
    </div>
    <ul class="navbar-nav flex-row" v-if="!user.isLogin">
      <li class="nav-item mx-1" v-for="btn in navBtns" :key="btn.name">
        <button
          :class="`btn btn-${btn.color}`"
          type="submit"
          @click="navigateTo(btn.path)"
        >
          {{btn.name}}
        </button>
      </li>
    </ul>
    <ul class="navbar-nav flex-row" v-else>
      <li class="nav-item mx-1">
        <dropdown :title="`你好 ${user.username}`" >
          <dropdown-item>
            <div @click="handleLogout">退出登陆</div>
          </dropdown-item>
        </dropdown>
      </li>
    </ul>
  </nav>
</header>
</template>

<script lang='ts'>
import { defineComponent, ref, PropType } from 'vue'
import Dropdown from './Dropdown.vue'
import DropdownItem from './DropdownItem.vue'
import { useRouter } from 'vue-router'
import { useStore } from 'vuex'
import { userProp } from '@/store/type'
import useCreateToast from '@/hooks/useCreateToast'

export default defineComponent({
  components: { Dropdown, DropdownItem },
  name: 'GlobalHeader',
  props: {
    user: {
      type: Object as PropType<userProp>,
      required: true
    }
  },
  setup () {
    const router = useRouter()
    const store = useStore()
    const navList = [
      { name: '首页', path: '/index' },
      {
        name: '专栏',
        path: '/column'
      },
      { name: '关于', path: '/About' }
    ]
    const cIndex = ref(0) // 当前导航栏选择下标
    const navBtns = [
      { name: '登录', path: '/login', color: 'primary' },
      { name: '注册', path: '/register', color: 'secondary' }
    ]
    const handleNavbar = (i: number) => { cIndex.value = i }
    const navigateTo = (path: string) => { router.push(path) }
    const handleLogout = () => {
      store.commit('logout')
      useCreateToast('成功退出登录！', 'success', 1000)
      router.replace('/index')
    }
    return {
      navList,
      cIndex,
      navBtns,
      handleNavbar,
      navigateTo,
      handleLogout
    }
  }
})
</script>

<style scoped>
.navbar {
  width: 75em;
  margin: 0 auto;
  padding: 0;
}
.nav a{
  color: #212529;
  text-decoration: none;
  padding: 0.8em 0;
}
.column-center > .c-item {
  padding: 0.8em 0;
  margin: 0 1.25em;
}
.column-center > .active {
  font-size: 16px;
  font-weight: 600;
}
.nav-active {
  font-size: 16px;
  font-weight: 600;
  border-bottom: 2px solid #007bff;
}
</style>
