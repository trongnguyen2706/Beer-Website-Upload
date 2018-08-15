<template>
  <div id="app" class="flex flex-wrap list">
    <div class="w-1/4 list">
    <List />
    </div>
    <div class="w-3/4 detail">
      <div class="top-detail w-full">
        <nuxt/>
    </div>
    </div>
  </div>
</template>
<script>
import List from '~/components/List'
export default {
    components: {
        List 
    },  
}
</script>

<style>

.detail {
    background-color: #F3F6E7;
}
.top-detail {
    background-image: url('http://rushriverbeer.com/wp-content/uploads/2015/04/OurBrews_Hearder_V21.jpg');
    height:20%;
}
</style>
