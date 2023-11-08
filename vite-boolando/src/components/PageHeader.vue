<script>
export default {
    data() {
        return {
            categories: ['Donna', 'Uomo', 'Bambino']
        }
    }
}
</script>

<template>
    <div class="container">
        <div class="row">
            <div class="col-1">
                <ul class="categories-list">
                    <li v-for="section in categories">
                        <a href="#">{{ section }}</a>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<style lang="scss">
/* CSS va qui! */
.categories-list {
    display: flex;
    gap: 15px;
}
</style>