<script setup>
import heroImg from "@/assets/images/content/hero.jpg";
import twiImg from "@/assets/images/icons/twi.svg";
import igImg from "@/assets/images/icons/ig.svg";
import fbImg from "@/assets/images/icons/fb.svg";

const content = {
    image: heroImg,
    title: "<span>M</span>idnight <span>R</span>oamer",
    subtitle: " Journeys After Dark, For the Ones Who Wander",
    text: `When the city sleeps, adventure begins. Midnight Roamer curates unforgettable night escapes—urban prowls, forest treks, and starlit retreats designed for curious souls and restless hearts.<br>
    Step into the shadows, chase the horizon, and roam where few dare.<br>
    Every trip is a story waiting to unfold. For the tripster in you—this is your hour.`,
    socials: [
        { icon: twiImg, link: "https://twitter.com" },
        { icon: igImg, link: "https://www.instagram.com" },
        { icon: fbImg, link: "https://www.facebook.com" },
    ],
};
</script>

<template>
    <section class="hero" :style="`background-image: url('${content.image}')`">
        <div class="container">
            <div class="hero__wrapper">
                <div class="hero__body">
                    <h1 class="hero__title" v-html="content.title"></h1>
                    <div class="hero__subtitle">{{ content.subtitle }}</div>
                    <div class="hero__text" v-html="content.text"></div>
                </div>
                <div class="hero__bottom">
                    <div class="hero__scroll">Scroll</div>

                    <!-- SOCIALS -->
                    <div class="hero__social">
                        <a
                            v-for="(item, index) in content.socials"
                            :key="index"
                            :href="item.link"
                            class="hero__social-link"
                            target="_blank"
                        >
                            <img :src="item.icon" alt="socials image link" />
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<style lang="scss" scoped>
.hero {
    color: #fff;
    background-position: center center;
    background-size: cover;
    background-repeat: no-repeat;
    min-height: 100vh;
    margin-bottom: 100px;
    position: relative;
    z-index: 10;
    &:after {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.4);
        z-index: -1;
    }

    &__wrapper {
        min-height: 100vh;
        padding-top: 200px;
        display: flex;
        flex-direction: column;

        @media (max-width:  #{$md3}) {
            padding-top: 200px;
        }
        @media (max-width:  #{$md4}) {
            padding-top: 180px;
        }
        @media (max-height: 650px) {
            padding-top: 160px;
        }
    }

    &__body {
        // max-width: 643px;
        max-width: 850px;
        margin: 0 auto;
        text-align: center;
        flex: 1 1 auto;
    }

    &__title {
        font-family: "Noe Display";
        font-weight: 700;
        font-size: 110px;
        letter-spacing: -0.02em;
        margin-bottom: 48px;

        @media (max-width:  #{$md2}) {
            font-size: 100px;
        }

        @media (max-width: 600px) {
            font-size: calc(64px + (120 - 64) * ((100vw - 320px) / (600 - 320)));
            margin-bottom: 25px;
        }
    }

    &__subtitle {
        // @extend %Larsseit-Bold;
        font-size: 18px;
        line-height: 24px;
        letter-spacing: 0.1em;
        text-transform: uppercase;
        margin-bottom: 50px;

        @media (max-width:  #{$md4}) {
            font-size: 11px;
            margin-bottom: 25px;
        }
    }

    &__text {
        font-size: 17px;
        // line-height: 150%;
        line-height: 1.7;
        @media (max-width:  #{$md4}) {
            font-size: 12px;
        }
        @media (max-height: 650px) {
            margin-bottom: 50px;
        }
    }

    &__bottom {
        display: flex;
        justify-content: space-between;
        padding-bottom: 100px;
        @media (max-width:  #{$md4}) {
            padding-bottom: 60px;
        }
    }

    &__scroll {
        margin-left: 20px;
        margin-top: 15px;
        // @extend %Larsseit-Bold;
        font-size: 15px;
        letter-spacing: 0.05em;
        color: rgba($color: #ffffff, $alpha: 0.9);
        transform: rotate(-90deg);
        text-transform: uppercase;
        position: relative;
        &:after {
            content: "";
            position: absolute;
            top: 7px;
            left: -100px;
            background-color: $skyblue2;
            width: 80px;
            height: 2px;
            @media (max-width:  #{$md4}) {
                width: 60px;
                left: -75px;
            }
        }
        &:before {
            content: "";
            position: absolute;
            // bottom: 0px;
            left: -106px;
            width: 0;
            height: 0;
            border-left: 9px solid transparent;
            border-right: 9px solid transparent;
            border-bottom: 16px solid $skyblue2;
            transform: rotate(-90deg);
            @media (max-width:  #{$md4}) {
                left: -78px;
            }
        }
    }

    &__social {
        display: flex;
        flex-direction: column;
        align-items: center;
        row-gap: 22px;
    }

    &__social-link {
        transition: all 0.3s;
        &:hover {
            opacity: 0.5;
        }
    }
}
</style>

<style>
.hero__title span {
    color: #00c9e0;
}
</style>
