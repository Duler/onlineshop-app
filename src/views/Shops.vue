  
<template>
<div class="mt-5 container">
    <h2 class="title" >All shops</h2>
    <Search style ="float-right" @search-updated="onSearchTermChanged"/>
  <div class="row">
    <div class="col-md-7 card" style="height:30" v-for="shop in shops" :key="shop.id">
      <img class="card-img-top" :src="shop.image_url" alt="Card image cap" width="300" height="300">
      <div class="card-body">
      <a class="nav-link" @click="navigateToShop(shop.id)">{{shop.name}}</a>
      <div v-if="shop.manager_id">
        <a class="link-streched" @click="navigateToManager(shop.manager_id)">
          MANAGER: <br> {{shop.manager.first_name + ' ' + shop.manager.last_name}}
        </a>
      </div>
      <p v-else> Manager Required </p>
      </div>
    </div>
  </div>

</div>
</template>
<script>
import Search from './Search'
import {mapGetters,mapActions} from 'vuex'
export default {
  name: 'shops',
  components: {
    Search
  },
  computed: {
    ...mapGetters({
      shops: 'shops',
    }),
  },
  methods: {
    ...mapActions({
      fetchShops: 'fetchShops',
    }),
    onSearchTermChanged(term) {
      this.fetchShops(term)
    },
    navigateToManager(id) {
      this.$router.push({
        name: 'manager',
        params: {id}
      })
    },
    navigateToShop(id) {
      this.$router.push({
        name: 'shop',
        params: {id}
      })
    }
  },
  beforeRouteEnter(to, from, next) {
    next(vm => vm.fetchShops())
  }
}
</script>

<style>
  .title {
    padding:15px;
  }
  .card {
    padding:10px;
  }
</style>