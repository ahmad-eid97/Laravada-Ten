<template>
    <section class="slider-wrapper p-0">
            <!-- Wrapper For Slides -->
                    <VueSlickCarousel :fade="true" ref="c1" :asNavFor="$refs.c2" :arrows="false" :slidesToShow="1" :focusOnSelect="true" :dots="false" class="main" >
                        <div class="item" :style="image1">
                            
                        </div>
                        <div class="item" :style="image2">
                            
                        </div>
                        <div class="item" :style="image3">
                        </div>
                    </VueSlickCarousel>
                <!-- Indicators -->
                    <VueSlickCarousel
                        ref="c2"
                        v-show="c1"
                        :asNavFor="$refs.c1"
                        :slidesToShow="5"
                        :focusOnSelect="true" :dots="false" :arrows="false" class="thumb">
                            <img src="https://the7.io/modern-business/wp-content/uploads/sites/53/2018/12/t-img047.jpg" class="img-fluid">  
                            <img src="https://the7.io/modern-business/wp-content/uploads/sites/53/2018/12/t-img054.jpg" class="img-fluid"> 
                            <img src="https://the7.io/modern-business/wp-content/uploads/sites/53/2018/12/t-img050.jpg" class="img-fluid"> 
                    </VueSlickCarousel>
                    
                    <div class="text">
                        <h1>LARAVADA</h1>
                        <h2>The7 Modern Business</h2>
                        <p>Fusce dapibus congue diam – from dolor amet nulla dapibus interdum condimentum.</p>
                    </div>
        </section>
</template>

<script>
import VueSlickCarousel from 'vue-slick-carousel'
 import 'vue-slick-carousel/dist/vue-slick-carousel.css'; 
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'

export default {
    name: 'AppHomeSlider',
    components: {VueSlickCarousel},
    data() {
        return {
            c1: undefined,
            c2: undefined,
            image1: {backgroundImage: "url(https://the7.io/modern-business/wp-content/uploads/sites/53/2018/12/t-img047.jpg)"},
            image2: {backgroundImage: "url(https://the7.io/modern-business/wp-content/uploads/sites/53/2018/12/t-img054.jpg)"},
            image3: {backgroundImage: "url(https://the7.io/modern-business/wp-content/uploads/sites/53/2018/12/t-img050.jpg)"}
        }
    },
    methods : {
        
    },
    mounted() {
        this.c1 = this.$refs.c1;
        this.c2 = this.$refs.c2;
    },
}
</script>
<style lang="scss">

    .slider-wrapper {
        position: relative;
        background: var(--main-color);
    }
    .slider-wrapper .text {
        position: absolute;
        z-index: 4;
        color: #262d37;
        top: 0;
        height: 100%;
        width: 60%;
    }
    .slider-wrapper .text span {
        color: var(--main-color);
        
    }
    .slider-wrapper .text::after {
        position: absolute;
        background-color: #fff;
        width: 90%;
        content: '';
        height: 100%;
        top: 0;
        left: -80px;
        transform: skew(-15deg);
        z-index: -1;
    }
    .slider-wrapper .text::before {
        position: absolute;
        background-color: var(--main-color)6b;
        width: 83%;
        content: '';
        height: 100%;
        bottom: 0;
        left: 0px;
        transform: skew(15deg);
        z-index: -1;
    }
    .slider-wrapper h1 {
        font-size: 80px;
        position: relative;
        z-index: 2;
        margin: 100px 110px 0;
    }
    .slider-wrapper h2 {
        font-size: 34px;
        position: relative;
        z-index: 2;
        margin: 0 0 0 110px;
        padding: 20px 0;
        font-weight: 700;
    }
    .slider-wrapper p {
        font-size: 23px;
        position: relative;
        z-index: 2;
        margin: 0 0 0 110px;
        max-width: 300px;
    }

    @include sm {
        .slider-wrapper h1 {
            font-size: 50px;
            margin: 100px 110px 0 20px;
        }
        .slider-wrapper h2 {
            font-size: 25px;
            margin: 0 0 0 20px;
        }
        .slider-wrapper p {
            font-size: 18px;
            margin: 0 0 0 20px;
        }
    }
    .slider-wrapper .overlay {
        position: absolute;
        top: 0;
        z-index: 1;
        height: 100%;
        
    }
    .main .item {
        position: relative;
    }
    .main .item {
        min-height: 80vh;
        width: 100%;
        background-repeat: no-repeat;
        background-size: cover;
    }
    
    .thumb  {
        width: 400px;
        position: absolute !important;
        bottom: 0;
        right: 0;
        z-index: 3;
        background: var(--main-color);
        padding: 5px;
    }
    .thumb .slick-slide {
        padding: 5px;
        cursor: pointer;
    }
    .thumb img {
        border: 2px solid transparent;
    }
    .thumb img:hover {
        border: 2px solid #fff;
    }
    .thumb .slick-current img {
        border: 2px solid #fff;
    }
</style>