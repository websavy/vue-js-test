<template>
    <div>
        <div v-if="images.length>0" class="slider-grp">
            <div class="owl-carousel owl-theme">
                <div v-for="image in images">
                    <div class="item">
                        <img :src="image">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import 'owl.carousel/dist/assets/owl.carousel.min.css';
    import 'owl.carousel/dist/assets/owl.theme.default.min.css';
    import $ from 'jquery';
    import owlCarousel from 'owl.carousel';

    export default {
        name: 'slider',
        data () {
            return {
                images: []
            }
        },
        created(){
            let _this = this;

            $.getJSON(`/src/js/images.json`)
                .done(function (data) {

                    // Get the list of images
                    let imageList = data.images.path;
//              console.log(imageList);
                    _this.images = imageList;
                });
        },

        updated(){
//            Initialise the carousel
            $('.owl-carousel').owlCarousel({
                items: 3,
                loop: true,
                margin: 5,
                navText: [ '&#8249;', '&#8250;' ],
                nav: true,
                autoplay: true,
                autoplayTimeout: 3000,
                autoplayHoverPause: true,
                responsiveClass: true,
                responsive: {
                    0: {
                        items: 1,
                        nav: true
                    },
                    768: {
                        items: 2,
                        nav: true
                    },
                    992: {
                        items: 3,
                        nav: true
                    }
                }
            });
        }
    }
</script>
