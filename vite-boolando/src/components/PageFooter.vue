<script>
export default {
    data() {
        return {
            company: 'Boolando srl',
            links: ['Informazioni legali', 'Informazioni sulla privacy', 'Diritto di recesso'],
            findUs: 'Trovaci anche su',
            social: ['Twitter', 'Facebook', 'Instagram', 'Pinterest', 'Youtube']
        }
    }
}
</script>

<template>
    <div class="footer-content">
        <div class="container">
            <div class="row justify-beetween">
                <div class="info-container">
                    <div class="company">{{ company }}</div>
                    <ul class="info-links">
                        <li v-for="info in links">
                            <a href="#">{{ info }}</a>
                        </li>
                    </ul>
                </div>

                <div class="social-container">
                    <div class="find-us">{{ findUs }}</div>
                    <ul class="social-links">
                        <li v-for="social in socials">
                            <a href="#">{{ social }}</a>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped lang="scss">
@use '../style/partials/variables' as *;



.footer-content {
    height: 80px;
    background-color: $footer-color;
    color: white;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    font-size: 15px;

    .info-container {
        display: flex;
        flex-direction: column;
    }

    .company {
        font-size: 20px;
        font-weight: 600;
    }

    .info-links {
        display: flex;
        gap: 10px;

        a {
            color: white;
        }
    }
}

.social-container {
    display: flex;
    flex-direction: column;

    .find-us {
        font-size: 20px;
    }

    .social-links {
        display: flex;
        gap: 15px;
    }

    a {
        color: white;
    }
}
</style>