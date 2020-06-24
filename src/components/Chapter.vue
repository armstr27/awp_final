<template>
    <div class="chapter">
        <div class="chapter-title-div" @click="selectAll">
            <h3>Chapter {{chapter.number}}</h3>
        </div>
        <div class="grammar-point-div" v-for="point in chapter.points" v-bind:key="point.name">
            <GrammarPoint ref="grammarpoint" v-bind:point="point" v-on:select-point="$emit('select-point', point.name)" />
        </div>
    </div>
</template>

<script>
    import GrammarPoint from "./GrammarPoint";

    export default {
        name: "Chapter",
        components: {
            GrammarPoint
        },
        props: ["chapter"],

        methods: {
            selectAll() {
                this.$refs.grammarpoint.forEach(point => point.onPress());
            }
        }
    }

</script>

<style scoped>
    h3 {
        color: #c7d1e0;
        -moz-user-select: none;
        -khtml-user-select: none;
        -webkit-user-select: none;
    }

    .chapter-title-div {
        padding: 2vh;
    }

    .chapter {
        background: #062a37;
        /*padding: 3vh;*/
        border-left: 2px solid #c7d1e0;
        border-right: 2px solid #c7d1e0;
        border-bottom: 1px solid #c7d1e0;
        border-top: 1px solid #c7d1e0;
        border-radius:50px;

        cursor: pointer;
    }

    .grammar-point-div {
        border-radius:50px;
    }
</style>