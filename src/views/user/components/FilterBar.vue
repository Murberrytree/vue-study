<template>
  <div class="filter-bar control is-grouped">
    <p class="control is-expanded has-addons">
      <input id="search" class="input"
       type="text" v-model="filterText"
       @keyup.enter="doFilter"
       placeholder="이름 또는 이메일을 입력하세요">
      <a @click="doFilter" class="button is-primari">검색</a>
      <a @click="resetFilter" class="button">리셋</a>
    </p>
  </div>
</template>

<script>
  export default {
    name:'FilterBar',
    data () {
      return {
        filterText:''
      }
    },
    methods:{
      doFilter () {
        this.$events.fire('filter-set', this.filterText)
      },
      resetFilter () {
        this.filterText=''
        this.$events.fire('filter-reset')
      }
    }
  }
</script>

<style>
  #search {
    width:300px;
  }
</style>
