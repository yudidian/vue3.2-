<template>
  <div class="header">
    <!--    退出图标-->
    <img
      :src="closeType ? require('../../icons/svg/hamburger-opened.svg') : require('../../icons/svg/hamburger-closed.svg')"
      alt=""
      class="hamburger" @click="changeCloseType">
    <!--    面包屑-->
    <el-breadcrumb :separator-icon="ArrowRight">
      <el-breadcrumb-item :to="item.path" v-for="item in breadcrumbList" :key="item.path">{{
          item.path
        }}
      </el-breadcrumb-item>
    </el-breadcrumb>
    <!--    头像-->
    <el-avatar class="avatar" shape="square" :size="50"
               src="https://ts1.cn.mm.bing.net/th?id=OIP-C.bzgSr4mZFexX7i59eid9cgAAAA&w=204&h=204&c=8&rs=1&qlt=90&o=6&dpr=1.3&pid=3.1&rm=2"></el-avatar>
    <!--    下拉菜单-->
    <el-dropdown placement="bottom" class="dropdown">
      <span class="el-dropdown-link"></span>
      <template #dropdown>
        <el-dropdown-menu>
          <el-dropdown-item @click="logOut">退出</el-dropdown-item>
        </el-dropdown-menu>
      </template>
    </el-dropdown>
  </div>
</template>

<script setup>
import { useStore } from 'vuex'
import { useRoute } from 'vue-router'
import { ref, watch, computed } from 'vue'
import { ArrowRight } from '@element-plus/icons-vue'

const store = useStore()
const route = useRoute()
const breadcrumbList = ref([])
const closeType = computed(() => {
  console.log(closeType)
  return store.getters.closeType
})
const initBreadcrumbList = () => {
  breadcrumbList.value = route.matched
}

watch(route, () => {
  initBreadcrumbList()
}, {
  deep: true,
  immediate: true
})
const logOut = () => {
  store.dispatch('app/logOut')
}
const changeCloseType = () => {
  store.dispatch('app/changeCloseType')
}
</script>

<style scoped lang="scss">
.header {
  display: flex;
  height: 60px;
  align-items: center;
  text-align: right;

  .hamburger {
    margin-left: 10px;
    margin-right: 20px;
    width: 36px;
    height: 36px;
  }

  .avatar {
    flex: 1;
    text-align: right;

    &::v-deep img {
      margin-left: auto;
      margin-right: 10px;
    }
  }

  .dropdown {
    position: fixed;
    top: 0;
    right: 20px;
    width: 60px;
    height: 60px;
    z-index: 99;

    span {
      display: block;
      width: 60px;
      height: 60px;
    }
  }
}
</style>
