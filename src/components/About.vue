<script setup>
import { ref } from "vue";
import person1 from "@/assets/images/content/about-1.jpg";
import person2 from "@/assets/images/content/about-2.jpg";
import person3 from "@/assets/images/content/about-3.jpg";
import person4 from "@/assets/images/content/about-4.jpg";

const content = {
    title: "<span>A</span>bout <span>U</span>s",
    texts: [
        "We’re a team of four passioned people.",
        "We’re ready to take the world by storm and let you find new travel opportunities.",
        "Our everyday task is to make sure that you are satisfied with the services and products that we provide.",
        "With 💖 from Seattle, United States.",
    ],
    button: { link: "", title: "Learn more about us" },
    team: [
        { image: person1, name: "Martin Jacobs", position: "CEO" },
        { image: person2, name: "Priya Rapali", position: "Manager" },
        { image: person3, name: "Lucy Meadows", position: "Manager" },
        { image: person4, name: "Josef Schwab", position: "CTO" },
    ],
};

const hoveredItem = ref(0);
</script>

<template>
    <section class="about" id="about">
        <div class="container">
            <div class="about__wrapper">
                <div class="about__body">
                    <div class="section-title about__title" v-html="content.title"></div>
                    <div class="about__text">
                        <p v-for="(item, index) in content.texts" :key="index">
                            {{ item }}
                        </p>
                    </div>
                    <a :href="content.button.link" class="about__button button">{{ content.button.title }}</a>
                </div>

                <!-- TEAM MEMBERS -->
                <div class="about__items">
                    <div
                        v-for="(item, index) in content.team"
                        :key="index"
                        :class="`about__item ${index === hoveredItem ? 'hovered' : ''}`"
                        @mouseover="hoveredItem = index"
                    >
                        <div class="about__item-pic">
                            <img :src="item.image" alt="team member image" />
                        </div>
                        <div class="about__item-info">
                            {{ item.name.toUpperCase() }}, <span>{{ item.position.toUpperCase() }}</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<style lang="scss" scoped>
.about {
    margin-bottom: 240px;

    @media (max-width: #{$md2}) {
        margin-bottom: 100px;
    }
    @media (max-width: #{$md3}) {
        margin-bottom: 50px;
    }

    &__wrapper {
        display: flex;
        max-width: 1200px;
        margin: 0 auto;
        column-gap: 90px;

        @media (max-width: #{$md2}) {
            flex-direction: column;
        }
    }

    &__body {
        flex: 0 1 321px;
        margin-top: 56px;

        @media (max-width: #{$md1}) {
            flex: 0 0 321px;
        }
        @media (max-width: #{$md2}) {
            margin-bottom: 60px;
            flex: 1 1 100%;
        }
    }

    &__title {
        margin-bottom: 50px;
    }

    &__text {
        p + p {
            margin-top: 30px;
        }
        p:first-child,
        p:last-child {
            font-family: "Larsseit-Bold", "Helvetica Neue", Helvetica, Arial, sans-serif;
        }
        p {
            line-height: 150%;
        }
        font-family: "Larsseit-Light", sans-serif;
        font-size: 17px;
        letter-spacing: -0.02em;
        margin-bottom: 45px;
        @media (max-width: #{$md4}) {
            font-size: 16px;
        }
    }

    &__button {
        font-size: 14px;
        font-family: "Larsseit-Bold", "Helvetica Neue", Helvetica, Arial, sans-serif;
        font-weight: light;
    }

    &__items {
        flex: 0 1 790px;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        position: relative;
        &:after {
            content: "";
            position: absolute;
            top: 165px;
            right: -85px;
            background: url("@/assets/images/icons/dots.svg") 0 0 no-repeat;
            width: 70px;
            height: 470px;

            @media (max-width: #{$md1}) {
                top: 52px;
            }
            @media (max-width: #{$md2}) {
                top: auto;
                bottom: -290px;
                right: 330px;
                transform: rotate(90deg);
            }
            @media (max-width: #{$md3}) {
                display: none;
            }
        }

        @media (max-width: #{$md2}) {
            flex: 1 1 100%;
        }
    }

    &__item {
        flex: 1 1 50%;
        position: relative;
        &:after {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            background-color: #011627;
            opacity: 0.6;
            width: 100%;
            height: 100%;
            transition: all 0.5s;
        }

        &:hover {
            &:after {
                opacity: 0;
            }
            .about__item-info {
                opacity: 1;
                visibility: visible;
            }
        }

        @media (max-width: #{$md2}) {
            max-height: 375px;
            overflow: hidden;
        }
        @media (max-width: #{$md4}) {
            flex: 1 1 100%;
        }
    }

    &__item-pic {
        width: 100%;
        img {
            max-width: 100%;
        }

        @media (max-width: #{$md4}) {
            max-height: 375px;
            img {
                width: 100%;
            }
        }
    }

    &__item-info {
        display: inline-block;
        position: absolute;
        bottom: 50px;
        left: -50px;
        font-size: 15px;
        letter-spacing: 0.05em;
        color: #000000;
        background-color: #fff;
        padding: 26px 19px;
        border-radius: 8px;
        box-shadow: 5px 15px 40px rgba(0, 201, 224, 0.2);
        transition: all 0.5s;
        opacity: 0;
        visibility: hidden;
        span {
            color: $skyblue;
        }

        @media (max-width: #{$md2}) {
            left: 20px;
            bottom: 20px;
        }
        @media (max-width: 600px) {
            font-size: 13px;
            padding: 13px;
            left: 10px;
            bottom: 10px;
        }
        @media (max-width: #{$md4}) {
            left: 20px;
            bottom: 20px;
            font-size: 15px;
        }
    }
}

.hovered.about__item:after {
    opacity: 0;
}
.hovered .about__item-info {
    opacity: 1;
    visibility: visible;
}
</style>

<style>
.about__title span {
    color: #00c9e0;
}
</style>
