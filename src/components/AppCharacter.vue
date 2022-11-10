<script>
export default {
    name: "AppCharacter",
    props: { character: Object },
    data() {
        return {

        }
    }
}
</script>
<template>
    <div class="ms-bd-card">
        <img :src="character.img" alt="`foto di ${character.name}`">
        <p class="char-name ms-sub">{{ character.name }}</p>
        <p class="ms-sub ms-cat">{{ character.category }}</p>
        <p class="ms-sub">{{ character.status }}</p>
    </div>
</template>
<style lang="scss" scoped>
.ms-bd-card {
    width: 95%;
    margin: 0 auto;
    text-align: center;
    padding-bottom: 1.5rem;
    padding-top: 0.5rem;

    img {
        max-width: 100%
    }

    .ms-sub {
        margin: 0;
        padding: 0;
        display: block;
        font-size: 0.8rem;
    }

    .char-name {
        margin-top: 0.8rem;
        margin-bottom: 1.2rem;
        text-transform: uppercase;
        font-weight: bold;
        color: white;
        font-size: 0.6rem;
    }


    .ms-cat {
        margin-bottom: 0.5rem;
    }


}
</style>