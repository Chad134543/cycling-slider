<template>
    <div class="slide">
        <img class="movie-cover" :src="slide.coverSrc">
        <div class="movie-cover-bottom-edge"></div>
        <div class="info">
            <div class="title">{{ slide.title }}</div>
            <img class="rating-icon" :src="slide.ratingSrc">
            <span class="runtime">{{ slide.runtime }}</span>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Slide',
        data () {
            return {}
        },
        props: ['slide']
    }
</script>

<style>
    .slide {
        display: inline-block;
        width: 12.3%;
        height: 100%;
        margin-right: 2%;
        position: relative;
        left: -20.5%;
    }
    .slideinslideout-enter,
    .slideinslideout-leave-to {
        width: 0%;
        margin-right: 0;
    }
    .slideinslideout-enter-active,
    .slideinslideout-leave-active {
        transition: all 0.1s;
    }
    .slideinslideout-enter-active .info,
    .slideinslideout-leave-active .info {
        display: none;
    }
    .movie-cover {
        display: block;
        width: 100%;
        height: auto;
        box-shadow: 0 3px 5px rgba(0,0,0,0.6);
    }
    .movie-cover-bottom-edge {
        width: 100%;
        height: 1px;
        background-color: black;
    }
    .info {
        padding-top: 6%;
        font-size: 0.9vw;
        white-space: normal;
        position: absolute;
        width: 100%;
        height: 31%;
        left: 0;
        bottom: 0;
    }
    .title {
        margin-bottom: 0.1vw;
    }
    .rating-icon {
        width: auto;
        height: 0.7vw;
        position: relative;
        top: 0.06vw;
        margin-left: 0.05vw;
    }
    .runtime {
        font-size: 0.65vw;
        color: #D5D8DC;
        margin-left: 0.4vw;
    }
</style>