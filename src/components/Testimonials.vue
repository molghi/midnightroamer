<script setup>
import { ref, onMounted, onUnmounted } from "vue";

import { Swiper, SwiperSlide } from "swiper/vue";
import { Autoplay, Navigation } from "swiper/modules";
import "swiper/css";
import "swiper/css/navigation";

import person1 from "@/assets/images/content/author.jpg";
import person2 from "@/assets/images/content/author-2.jpg";
import person3 from "@/assets/images/content/author-3.jpg";
import person4 from "@/assets/images/content/author-4.jpg";

const content = {
    title: "<span>P</span>eople’s <span>T</span>houghts",
    subtitle: "SEE WHAT OTHERS ARE SAYING",
    testimonials: [
        {
            paragraphs: [
                "Midnight Roamer’s ‘Chill Adventure’ was the perfect mix of silence and sensation. The trip gave me something I didn’t know I needed—time to slow down without ever getting bored. The landscapes were dreamlike, and the guides struck that rare balance between laid-back and laser-focused.",
                "I remember sitting beside a fire on the edge of a cliff, watching stars slide across the sky in silence. No notifications. No lights. Just the night. You return from these trips changed, calmer, sharper somehow. Can’t recommend it enough.",
            ],
            name: "Jamie L.",
            position: "32, Berlin",
            image: person1,
        },
        {
            paragraphs: [
                "I joined ‘Spooky Times’ out of curiosity, and I left with a wild story and goosebumps that lasted days. Wandering through a misty forest at midnight while listening to eerie folklore felt like stepping into another world. The suspense was crafted brilliantly—it was immersive, never forced.",
                "What struck me most was the mood—the way the surroundings, storytelling, and group energy all combined into something genuinely unforgettable. I thought it was just a gimmick trip. I was wrong. It was a full-sensory, slow-burn experience that still haunts me in the best way.",
            ],
            name: "Andrea M.",
            position: "29, Cape Town",
            image: person2,
        },
        {
            paragraphs: [
                `‘Out in the Wild’ was the closest I’ve felt to real freedom in years. No clocks, no screens—just the rhythm of nature and a crew that knew how to disappear into it. Every moment felt raw and alive. I didn’t expect to feel so grounded sleeping under the stars, but it was exactly what I needed.`,
                `Waking up to fog over the valley and the smell of pine is something I’ll never forget. There’s a quiet kind of magic in being unplugged and out there. Midnight Roamer doesn’t do tourism. They guide you into an experience that feels ancient and personal.`,
            ],
            name: "Sofia R.",
            position: "28, Melbourne",
            image: person3,
        },
        {
            paragraphs: [
                `‘Desert Madness’ lives up to its name in the best way possible. The silence of the desert at night is something electric—you hear your own heartbeat, your thoughts shift gears. The bonfire stops being about warmth and becomes a kind of anchor to reality.`,
                `We rode through alien landscapes, shared wild stories, and fell into a rhythm that made time feel irrelevant. It’s not just about adventure—it’s about shedding layers. Midnight Roamer isn’t for the casual traveler. It’s for those ready to feel something deep and real.`,
            ],
            name: "Malik T.",
            position: "37, Toronto",
            image: person4,
        },
    ],
};

const isDesktop = ref(window.innerWidth > 992);

const updateScreen = () => (isDesktop.value = window.innerWidth > 992);

onMounted(() => window.addEventListener("resize", updateScreen));

onUnmounted(() => window.removeEventListener("resize", updateScreen));
</script>

<template>
    <section class="thoughts" id="thoughts">
        <div class="another-container">
            <div class="thoughts__wrapper">
                <div class="section-title thoughts__title" v-html="content.title"></div>
                <div class="thoughts__subtitle">{{ content.subtitle }}</div>
                <!-- RENDER REVIEWS -->
                <div class="thoughts__items">
                    <div v-for="(item, index) in content.testimonials" :key="index" class="thoughts__item" v-if="isDesktop">
                        <div class="thoughts__item-text">
                            <p v-for="(element, index) in item.paragraphs" :key="index">
                                {{ element }}
                            </p>
                        </div>
                        <div class="thoughts__item-author">
                            <div class="thoughts__item-pic">
                                <img :src="item.image" alt="testimonials author img" />
                            </div>
                            <div class="thoughts__item-box">
                                <div class="thoughts__item-name">{{ item.name }}</div>
                                <div class="thoughts__item-position">{{ item.position }}</div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- ACTIVATE SWIPER ON SMALL SCREENS -->
                <swiper
                    v-if="!isDesktop"
                    :modules="[Autoplay, Navigation]"
                    navigation
                    :loop="true"
                    :autoplay="{ delay: 3000, disableOnInteraction: false }"
                    :slides-per-view="1"
                    :space-between="16"
                    :breakpoints="{
                        992: {
                            slidesPerView: 'auto', // for large screens: no slider
                            enabled: false, // disable swiper on ≥992px
                        },
                        0: {
                            slidesPerView: 1,
                            enabled: true, // enable swiper on <992px
                        },
                    }"
                >
                    <swiper-slide v-for="(item, index) in content.testimonials" :key="index">
                        <div class="thoughts__item">
                            <div class="thoughts__item-text">
                                <p v-for="(element, index) in item.paragraphs" :key="index">
                                    {{ element }}
                                </p>
                            </div>
                            <div class="thoughts__item-author">
                                <div class="thoughts__item-pic">
                                    <img :src="item.image" alt="testimonials author img" />
                                </div>
                                <div class="thoughts__item-box">
                                    <div class="thoughts__item-name">{{ item.name }}</div>
                                    <div class="thoughts__item-position">{{ item.position }}</div>
                                </div>
                            </div>
                        </div>
                    </swiper-slide>
                </swiper>
            </div>
        </div>
    </section>
</template>

<style lang="scss" scoped>
.thoughts {
    color: #fff;
    // padding-bottom: 100px;
    &__wrapper {
        background-color: #011627;
        padding: 100px 0 0 0;
    }

    &__title {
        text-align: center;
        margin-bottom: 31px;
        position: relative;
        &:after {
            content: "";
            position: absolute;
            top: -160px;
            left: 50%;
            background-color: $skyblue;
            width: 2px;
            height: 80px;
        }
        @media (max-width: #{$md2}) {
            &:after {
                top: -95px;
            }
        }
        @media (max-width: #{$md3}) {
            &:after {
                top: -110px;
            }
        }
        @media (max-width: 600px) {
            font-size: 41px;
        }
    }

    &__subtitle {
        // @extend %Larsseit-Bold;
        font-size: 24px;
        line-height: 150%;
        text-align: center;
        letter-spacing: 0.15em;
        margin-bottom: 73px;
        @media (max-width: 600px) {
            font-size: 15px;
        }
        @media (max-width: #{$md4}) {
            margin-bottom: 45px;
        }
    }

    &__items {
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
        max-width: 1044px;
        margin: 0 auto;
        gap: 24px;
        margin-bottom: 100px;
        @media (max-width: #{$md1}) {
            padding: 0 24px;
        }
        @media (max-width: #{$md2}) {
            margin-bottom: 0;
        }
    }

    &__item {
        flex: 1 1 48%;
        background-color: #02223b;
        padding: 75px 75px 75px 102px;
        display: flex;
        flex-direction: column;
        @media (max-width: #{$md2}) {
            flex: 1 1 100%;
            padding: 37px 37px 37px 77px;
        }
        @media (max-width: #{$md4}) {
            padding: 37px;
        }
    }

    &__item-text {
        p:nth-child(1) {
            font-family: "Larsseit-Bold", "Helvetica Neue", Helvetica, Arial, sans-serif;
        }
        p + p {
            margin-top: 22px;
        }
        p {
            font-family: "Larsseit-Light", sans-serif;
            line-height: 190%;
        }
        flex-grow: 1;
        font-size: 18px;
        margin-bottom: 34px;
        position: relative;
        &:after {
            content: "";
            position: absolute;
            top: 0;
            left: -52px;
            background: url("@/assets/images/icons/commas.svg") 0 0 no-repeat;
            width: 32px;
            height: 25px;
        }
        @media (max-width: #{$md4}) {
            font-size: 14px;
            &:after {
                top: -30px;
                left: -30px;
            }
        }
    }

    &__item-author {
        display: flex;
        align-items: center;
    }

    &__item-pic {
        border-radius: 4px;
        overflow: hidden;
        margin-right: 12px;
        max-width: 80px;
        min-width: 80px;
        img {
            max-width: 100%;
        }
    }

    &__item-box {
    }

    &__item-name {
        font-size: 14px;
        letter-spacing: 0.15em;
        text-transform: uppercase;
        margin-bottom: 15px;
        @media (max-width: #{$md4}) {
            line-height: 1.25;
        }
    }

    &__item-position {
        font-size: 12px;
        letter-spacing: 0.15em;
        text-transform: uppercase;
        line-height: 1.4;
        font-family: "Larsseit-Light", sans-serif;

        @media (max-width: #{$md4}) {
            line-height: 1.25;
        }
    }
}

.another-container {
    max-width: 1680px;
    margin: 0 auto;
    // padding: 0 10px;
    @media (max-width: 1695px) {
        max-width: 1400px;
    }
}
</style>

<style lang="scss">
.thoughts .swiper {
    margin-bottom: 100px;
    padding: 0 20px;

    .swiper-button-prev:after,
    .swiper-button-next:after {
        font-size: 70px;

        @media (max-width: #{$md4}) {
            font-size: 40px;
        }
    }
}
</style>

<style>
.thoughts__title span {
    color: #00c9e0;
}
</style>
