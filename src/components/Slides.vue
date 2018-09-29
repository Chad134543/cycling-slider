<template>
    <div class="slides-component">
        <transition-group class="slides clearfix" name="slideinslideout" tag="div">
            <Slide v-for="s in slides" :key="s.id" :slide="s"></Slide>
        </transition-group>
        <div class="lip-left">
            <div class="lips-top"></div>
            <div class="lips-bottom"></div>
            <span></span>
        </div>
        <div class="lip-right">
            <div class="lips-top"></div>
            <div class="lips-bottom"></div>
            <span></span>
        </div>
        <div class="navigation">
            <div class="btn-prev" @click="moveToPrev">
                <svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
                     width="25px" height="27px" viewBox="0 0 25 27" enable-background="new 0 0 25 27" xml:space="preserve">
                    <path fill="#C42129" d="M10.642,13.501L24.996,0H14.363L0,13.499L14.36,27H25L10.642,13.501z"/>
                    <polygon fill="#FFFFFF" points="14.756,25.985 22.445,25.985 9.168,13.499 22.446,1.012 14.756,1.012 1.475,13.501 "/>
                </svg>
            </div>
            <div class="btn-next" @click="moveToNext">
                <svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
                     width="25px" height="27px" viewBox="0 0 25 27" enable-background="new 0 0 25 27" xml:space="preserve">
                    <path fill="#C42129" d="M0,27h10.64L25,13.499L10.637,0H0.004l14.354,13.501L0,27z"/>
                    <polygon fill="#FFFFFF" points="10.244,25.985 2.555,25.985 15.832,13.499 2.554,1.012 10.244,1.012 23.525,13.501 "/>
                </svg>
            </div>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue'
    import Slide from './Slide'

    export default {
        data () {
            return {
                slides: [
                    {
                        id: '1A',
                        coverSrc: 'static/img/Platoon.jpg',
                        title: 'Platoon',
                        runtime: '1 hr 53 min',
                        ratingSrc: 'static/img/rating-icon-r.png'
                    },
                    {
                        id: '2A',
                        coverSrc: 'static/img/RainMan.jpg',
                        title: 'Rain Man',
                        runtime: '2 hr 13 min',
                        ratingSrc: 'static/img/rating-icon-r.png'
                    },
                    {
                        id: '3A',
                        coverSrc: 'static/img/SchindlersList.jpg',
                        title: 'Schindler\'s List',
                        runtime: '3 hr 16 min',
                        ratingSrc: 'static/img/rating-icon-r.png'
                    },
                    {
                        id: '4A',
                        coverSrc: 'static/img/ForrestGump.jpg',
                        title: 'Forrest Gump',
                        runtime: '2 hr 22 min',
                        ratingSrc: 'static/img/rating-icon-pg13.png'
                    },
                    {
                        id: '5A',
                        coverSrc: 'static/img/ABeautifulMind.jpg',
                        title: 'A Beautiful Mind',
                        runtime: '2 hr 15 min',
                        ratingSrc: 'static/img/rating-icon-pg13.png'
                    },
                    {
                        id: '6A',
                        coverSrc: 'static/img/TheReturnOfTheKing.jpg',
                        title: 'The Return of the King',
                        runtime: '3 hr 21 min',
                        ratingSrc: 'static/img/rating-icon-pg13.png'
                    },
                    {
                        id: '7A',
                        coverSrc: 'static/img/NoCountryForOldMen.jpg',
                        title: 'No Country for Old Men',
                        runtime: '2 hr 2 min',
                        ratingSrc: 'static/img/rating-icon-r.png'
                    },
                    {
                        id: '8A',
                        coverSrc: 'static/img/Birdman.jpg',
                        title: 'Birdman',
                        runtime: '1 hr 59 min',
                        ratingSrc: 'static/img/rating-icon-r.png'
                    },
                    {
                        id: '9A',
                        coverSrc: 'static/img/Spotlight.jpg',
                        title: 'Spotlight',
                        runtime: '2 hr 9 min',
                        ratingSrc: 'static/img/rating-icon-r.png'
                    },
                    {
                        id: '10A',
                        coverSrc: 'static/img/TheShapeOfWater.jpg',
                        title: 'The Shape of Water',
                        runtime: '1 hr 59 min',
                        ratingSrc: 'static/img/rating-icon-r.png'
                    }

                ]
            }
        },
        components: {
            Slide
        },
        methods: {
            moveToPrev() {
                let that = this,
                    slide = this.slides[this.slides.length-1]

                that.slides.unshift(slide)
                slide.id = this.makeUniqueId(slide.id)
                slide = this.slides.pop()
            },
            moveToNext() {
                let that = this,
                    slide

                slide = this.slides.shift()
                slide.id = this.makeUniqueId(slide.id)
                that.slides.push(slide)
            },
            makeUniqueId(id) {  // Unique id/key required to achieve css transition.
                if (id[id.length-1]==='A') {
                    id = id.replace('A', 'B')
                } else {
                    id = id.replace('B', 'A')
                }
                return id
            }
        },
        mounted () {
            let that = this

            window.addEventListener('keydown', function(e){
                if (e.keyCode === 37) {
                    that.moveToPrev()
                } else if (e.keyCode === 39) {
                    that.moveToNext()
                }
            })
        }
    }
</script>

<style>
    .clearfix:before {
        content: " ";
        display: table;
    }
    .clearfix:after {
        content: " ";
        display: table;
        clear: both;
    }
    .slides-component {
        width: 100%;
        padding-bottom: 31.3%;
        position: relative;
        margin: 0 auto;
    }
    .slides {
        position: absolute;
        width: 100%;
        height: 85%;
        left: 0;
        right: 0;
        top: 15%;
        bottom: 0;
        text-align: left;
        overflow: hidden;
        white-space: nowrap;
    }
    .lip-left {
        width: 0.8%;
        height: 100%;
        position: absolute;
        left: 0;
        top: 0;
        background: linear-gradient(to right, rgba(0,0,0,0.2) 0%, rgba(0,0,0,0) 100%);
        border-left: 1px solid rgb(105,13,27);
    }
    .lip-right {
        width: 0.8%;
        height: 100%;
        position: absolute;
        right: 0;
        top: 0;
        background: linear-gradient(to right, rgba(0,0,0,0) 0%, rgba(0,0,0,0.2) 100%);
        border-right: 1px solid rgb(105,13,27);
    }
    .lips-top {
        position: absolute;
        width: calc(100% + 1px);
        height: 15%;
        top: 0;
        background: linear-gradient(to bottom, rgba(199,0,30,1) 0%, rgba(199,0,30,0) 100%);
    }
    .lips-bottom {
        position: absolute;
        width: calc(100% + 1px);
        height: 15%;
        bottom: 0;
        background: linear-gradient(to bottom, rgba(199,0,30,0) 0%, rgba(199,0,30,1) 100%);
    }
    .lip-left .lips-top,
    .lip-left .lips-bottom {
        left: -1px;
    }
    .lip-right .lips-top,
    .lip-right .lips-bottom {
        right: -1px;
    }
    .navigation {
        position: absolute;
        bottom: -60px;
        left: 0;
        right: 0;
        text-align: center;
        user-select: none;
    }
    .btn-prev,
    .btn-next {
        display: inline-block;
        margin: 0 10px;
        cursor: pointer;
    }
    .btn-prev svg,
    .btn-next svg {
        filter: drop-shadow( 0 2px 2px rgba(0,0,0,0.5) );
    }
</style>