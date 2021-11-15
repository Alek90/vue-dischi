<template>
    <main id="main_site" class="bg-dark">

        <div class="">
            <!-- qui inseriremo componente card. -->
            <DiscList />
        </div>

    </main>
</template>

<script>
import DiscList from './DiscsList.vue'


export default {

    name: 'MainSite',

    components: {
        DiscList
    }
}
</script>

<style lang="scss">

</style>