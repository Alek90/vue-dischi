<template>
    <main id="main_site">

        <div class="main_content container-fluid">

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