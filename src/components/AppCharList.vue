<script>
import { isStaticProperty } from "@vue/compiler-core";
import { getGlobalThis } from "@vue/shared";
import { resolveTransitionHooks, setTransitionHooks } from "vue";
import { store } from "../store"
import AppCharacter from "./AppCharacter.vue";
export default {
    name: "AppProductList",
    components: {
        AppCharacter
    },
    data() {
        return {
            store,
            printList: store.characters.filter(char => char.char_id < 5)
        }
    }
}</script>
<template>
    <div class="ms-box-char">
        <div class="char-news">
            <div>{{ this.store.characters.length }}Found Characters</div>

        </div>
        <div class="ms-box-char-small">
            <div class="container-fluid pt-2">
                <div class="row  ms-overflow flex-wrap">
                    <div class="col-2 ms-margin" v-for="element in store.characters" :key="element.char_id">
                        <AppCharacter :character="element" />
                    </div>
                </div>
            </div>
        </div>

    </div>


</template>
<style lang="scss" scoped>
@use "../styles/general.scss" as *;
@use"../styles/partials/variables" as*;

.ms-box-char {
    width: 80%;
    margin: 0 auto;
    padding: 2rem 2rem 1rem 2rem;
    background-color: white;
    height: 100%;
    overflow-y: auto;

    .char-news {
        color: white;
        background-color: #212529;
        padding: 0.5rem;
    }

    .ms-box-char-small {
        width: 98%;
        margin: 0 auto;
        background-color: white;
    }

    .col-2 {
        min-height: 100px;
        background-color: $bg-app;

        &.ms-right-not {
            margin-right: 0;
        }

        &.ms-margin {
            margin-right: calc(100% / 24 * 1);
            margin-bottom: calc(100% / 24 * 1);


        }

        &.ms-margin:nth-of-type(5n) {
            margin-right: 0px;
        }

    }
}
</style>