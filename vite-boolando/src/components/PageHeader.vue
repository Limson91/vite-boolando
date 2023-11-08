<script>
export default {
    data() {
        return {
            categories: ['Donna', 'Uomo', 'Bambino'],
            icons: ['Shop', 'Like', 'Cart']
        }
    }
}
</script>

<template>
    <div class="header-content">
        <div class="container">
            <div class="row">
                <ul class="list">
                    <li v-for="section in categories">
                        <a href="#">{{ section }}</a>
                    </li>
                </ul>

                <div class="col grow-1">
                    <img src="/boolean-logo.png" alt="">
                </div>
                <ul class="list">
                    <li v-for="icon in icons">
                        <a href="#">{{ icon }}</a>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<style scoped lang="scss">
@use '../style/partials/variables' as *;

.list {
    display: flex;
    gap: 15px;

    li {
        display: flex;
        align-items: center;
    }

    a {
        color: white;
    }
}

.col {
    display: flex;
    align-items: center;
    justify-content: center;

    img {
        width: 200px;
    }
}

.header-content {
    background-color: $header-color;
    width: 100vw;
    line-height: 75px;
    padding: 0px 20px;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}
</style>