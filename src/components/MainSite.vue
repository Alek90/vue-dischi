<template>
    <main id="main_site" class="bg-dark">

        <div class="main_content container-fluid">
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

#main_site{
    height: 100vh;

    .main_content{
        padding: 100px 0;
    }
}
</style>