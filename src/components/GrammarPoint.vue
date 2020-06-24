<template>
    <div class="grammar-point-div" v-bind:class="{'is-selected':this.selected}" @click="onPress()">
        <p class="unselectable">
            {{point.name}}
        </p>
    </div>
</template>

<script>
    export default {
        name: "GrammarPoint",
        props: ["point"],
        data() {
            return {
                selected: false
            }
        },
        methods: {
            onPress() {
                this.selected = !this.selected;
                this.$emit('select-point', this.$props.point.name);
            }
        }
    }
</script>

<style scoped>
    .grammar-point-div {
        background: #0d4d68;
        color: #c7d1e0;
        padding-top: 2vh;
        padding-bottom: 2vh;
        border: 2px solid #c7d1e0;
        cursor: pointer;
    }

    .is-selected {
        background: #2bbed1;
        color: #280623;
    }

    *.unselectable {
        -moz-user-select: none;
        -khtml-user-select: none;
        -webkit-user-select: none;

        /*
          Introduced in IE 10.
          See http://ie.microsoft.com/testdrive/HTML5/msUserSelect/
        */
        -ms-user-select: none;
        user-select: none;
    }
</style>