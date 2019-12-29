<template>
  <input type="text" 
  class="form-control mx-sm-3 float-right" 
  placeholder="Search..."  
  autocomplete="on"
  v-model="search" @input="searchUpdated($event.target.value)"/>
</template>

<script>
export default {    
    name: 'Search',
    data() {
      return {
        search: ''
      }
    },
    methods: {
        searchUpdated(search) {
        this.$emit('search-updated', search)
        }
    }
}
</script>
