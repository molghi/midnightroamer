<script setup>
const content = {
    title: "<span>S</span>ee you soon!",
    subtitle: "We hope to see you again<br>very soon.",
};
</script>

<template>
    <section class="prefooter">
        <div class="container">
            <div class="prefooter__wrapper">
                <div class="section-title prefooter__title" v-html="content.title"></div>
                <div class="prefooter__subtitle" v-html="content.subtitle"></div>
            </div>
        </div>
    </section>
</template>

<style lang="scss" scoped>
.prefooter {
    margin-bottom: 150px;

    &__wrapper {
    }

    &__title {
        margin-bottom: 40px;
        text-align: center;

        @media (max-width: #{$md4}) {
            font-size: 54px;
        }
    }

    &__subtitle {
        font-family: "Larsseit Bold", "Larsseit-Bold", "Helvetica Neue", Helvetica, Arial, sans-serif;
        font-size: 24px;
        line-height: 150%;
        text-align: center;
        letter-spacing: 0.07em;
        max-width: 388px;
        margin: 0 auto;
        position: relative;
        &:after {
            content: "";
            position: absolute;
            bottom: -150px;
            left: 50%;
            background-color: $skyblue;
            width: 2px;
            height: 80px;
        }
        @media (max-width: #{$md4}) {
            font-size: 20px;
            &:after {
                bottom: -120px;
            }
        }
    }
}
</style>

<style>
.prefooter__title span {
    color: #00c9e0;
}
</style>
