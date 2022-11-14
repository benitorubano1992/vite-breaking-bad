<script>
import { store } from "../store"
export default {
    name: "AppChoiceSerie",
    data() {
        return {
            store
        }
    }
}

</script>
<template>
    <div>
        <label for="series"></label>

        <select name="series" id="series" v-model="store.serieName" @change="$emit('selectSerie')">
            <option value="">Select category</option>
            <option value="Breaking Bad">Breaking Bad</option>
            <option value="Better Call Saul">Better Call Saul</option>
        </select>
    </div>
</template>
<style lang="scss" scoped>
label {
    display: none;
}
</style>