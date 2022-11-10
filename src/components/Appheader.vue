<script>
export default {
    name: "AppHeader",
    data() {
        return {

        }
    }
}
</script>
<template>
    <header class="d-flex">
        <img src="https://i.pinimg.com/originals/e4/64/7a/e4647ae03886b3acd7c203dd532d6f2b.png" alt="logo Breaking bad">
        <h1>Breaking Bad Api</h1>
    </header>
</template>
<style lang="scss" scoped>
@use "../styles/general.scss" as *;

header {
    img {
        height: 50px;
    }

    h1 {
        color: white;
        font-weight: bolder;
        margin-left: 0.5rem;
    }
}
</style>