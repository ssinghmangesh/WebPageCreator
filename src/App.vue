<template>
    <div id="app">
        <MainComponent/>
    </div>
</template>

<script>
import MainComponent from "./components/MainComponent";
export default {
    name: "App",

    components: {
        MainComponent
    }
};
</script>

<style>
* {
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
}
body,html {
    padding: 0;
    margin: 0;
    height: 100%;
    width: 100%;
}
#app {
    height: 100%;
    width: 100%;
}
</style>
