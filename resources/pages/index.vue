<template>
    <div id="app" class="flex flex-wrap list">
        <div class="w-full detail">
        <div class="top-detail w-full">

        </div>
        <h2><nuxt-child :key="$route.params.id"/></h2>
        </div>
    </div>
</template>
<script>

import Detailview from '@/components/Detailview'
export default { }
</script>

<style>

</style>

    
