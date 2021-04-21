<template>
    <div class="dot-menu">
        <button class="dot-menu__button"></button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            header: 'Menu2'
        }
    }
}
</script>

<style lang="scss">
    .dot-menu__button {
        width: 3px;
        height: 3px;
        border-radius: 50%;
        background-color: black;
    }
</style>