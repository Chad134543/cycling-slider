<template>
    <div id="app">
        <Slides />
    </div>
</template>

<script>
import Slides from './components/Slides'

export default {
    name: 'App',
    components: {
            Slides
        }
    }
</script>

<style>
    * {
        box-sizing: border-box;
    }
    body {
        padding: 10% 12% 0 12%;
        margin: 0;
        font-size: 14px;
        line-height: 1.3;
        background-color: rgb(199,0,30);
        color: #FFF;
    }
    #app {
        width: 100%;
        max-width: 1296px;
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        margin: 0 auto;
    }
</style>
