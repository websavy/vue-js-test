<template>
    <div id="app">
        <nav-vue></nav-vue>
        <slider-vue></slider-vue>
    </div>
</template>

<script>

    import Nav from './Header.vue'
    import Slider from './Slider.vue'

    export default {
        name: 'app',
        components: {
            'nav-vue': Nav,
            'slider-vue': Slider
        }
    }
</script>