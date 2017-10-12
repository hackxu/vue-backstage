<template>
  <div>
    <commonHeader></commonHeader>
    <div class="article_list">
      <ul>
        <li v-for="i in list">
          <time v-text="i.create_at"></time>
          <router-link :to="'/content/' + i.id">
            {{i.title}}
          </router-link>
        </li>
      </ul>
    </div>
    <commonFooter></commonFooter>
  </div>
</template>


<script>
  import commonHeader from '../components/header.vue'
  import commonFooter from '../components/footer.vue'

  export default {
    components: {commonHeader, commonFooter},
    data () {
      return {
        list: []
      }
    },
    created () {
      this.getData()
    },
    methods: {
      getData () {
        this.$api.get('topics', null, r => {
          this.list = r.data
        })
      }
    }
  }
</script>
