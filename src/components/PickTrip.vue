<script setup>
import { ref, watch, nextTick } from "vue";
import twiImg from "@/assets/images/icons/twi.svg";
import igImg from "@/assets/images/icons/ig.svg";
import fbImg from "@/assets/images/icons/fb.svg";

import image1 from "@/assets/images/content/pick-1.jpg";
import image2 from "@/assets/images/content/pick-2.jpg";
import image3 from "@/assets/images/content/pick-3.jpg";
import image4 from "@/assets/images/content/pick-4.jpg";
import image5 from "@/assets/images/content/pick-5.jpg";
import image6 from "@/assets/images/content/pick-6.jpg";
import image7 from "@/assets/images/content/pick-7.jpg";
import image8 from "@/assets/images/content/pick-8.jpg";

import { Swiper, SwiperSlide } from "swiper/vue";
import { Autoplay, Navigation } from "swiper/modules";
import "swiper/css";
import "swiper/css/navigation";

const content = {
    title: "<span>P</span>ick <span>Y</span>our <span>T</span>rip",
    subtitle: "Our team has put together great trips for you to discover!",
    shareBlockText: "SHARE IT:",
    triggers: [
        { title: "Chill Adventure", href: "#chill" },
        { title: "Spooky Times", href: "#spooky" },
        { title: "Desert Madness", href: "#desert" },
        { title: "Out in the Wild", href: "#wild" },
    ],
    texts: [
        { id: "chill", title: "Beautiful Oasis" },
        { id: "spooky", title: "" },
        { id: "desert", title: "" },
        { id: "wild", title: "" },
    ],
    socials: [
        { link: "/", icon: twiImg },
        { link: "/", icon: igImg },
        { link: "/", icon: fbImg },
    ],
    tabContents: [
        {
            slidesViews: [
                { title: "Grand Dunes Landscape", image: image1 },
                { title: "Beautiful Oasis", image: image2 },
            ],
            body: {
                title: "<span>C</span>hill <span>A</span>dventure",
                texts: [
                    "Laid-back nights. Easy trails. Deep vibes. Slow it down and breathe it in. Chill Adventure is for those who roam without rushing—where twilight trails, quiet shores, and low-key campfires create space to reset.",
                    "No pressure, no pace. Just open skies, ambient stops, and the kind of moments that feel unplanned but stay unforgettable.",
                    "Perfect for solo thinkers, mellow crews, or anyone chasing calm beyond the city glow.",
                ],
                buttonTitle: "SEE OUR LATEST OFFER",
            },
        },
        {
            slidesViews: [
                { title: "Haunted Trails & Twilight Skies", image: image3 },
                { title: "Ghostly Paths Through Foggy Pines", image: image6 },
            ],
            body: {
                title: "<span>S</span>pooky <span>T</span>imes",
                texts: [
                    "Night falls. Shadows stretch. Nerves tingle. For those who lean into the eerie. Spooky Times blends mystery with thrill—midnight ruins, foggy forests, strange tales by firelight.",
                    "Expect ghost lore, creaking paths, and a sense that you're not entirely alone. Low lights, high tension. Come if you dare.",
                ],
                buttonTitle: "BOOK NOW",
            },
        },
        {
            slidesViews: [
                { title: "A Vivid Sunset Like Melted Iron", image: image4 },
                { title: "Gold Sands At Night", image: image5 },
            ],
            body: {
                title: "<span>D</span>esert <span>M</span>adness",
                texts: [
                    "Heat lingers. Silence hums. The surreal unfolds. This one’s all about extremes—red sands under moonlight, echoing canyons, and stillness so deep it roars.",
                    "Desert Madness is the mind-bending, mirage-chasing escape for the wild at heart. Stare into stars that never blink, ride winds that whisper strange truths, and find clarity in the chaos.",
                ],
                buttonTitle: "SEE OUR LATEST OFFER",
            },
        },
        {
            slidesViews: [
                { title: "Raw Earth & Untamed Forest", image: image7 },
                { title: "Wilderness Echoes for the Brave", image: image8 },
            ],
            body: {
                title: "<span>O</span>ut in the <span>W</span>ild",
                texts: [
                    "No fences. No filters. Just raw, remote earth. Out in the Wild strips it all back. Rugged trails, real terrain, and nights where your only ceiling is the sky.",
                    "It’s not curated—it’s carved. For the restless soul who feels most alive off-grid, under pine, or across peaks where signal dies and senses wake up.",
                ],
                buttonTitle: "BOOK NOW",
            },
        },
    ],
};

const activeTabTrigger = ref(0);
const mySwiper = ref(null);
const mySwipers = ref({});

// re-initialize Swiper’s navigation module
// watch(activeTabTrigger, async () => {
//     await nextTick();
//     if (mySwiper.value && mySwiper.value.swiper) {
//         const swiperInstance = mySwiper.value.swiper;
//         swiperInstance.navigation.destroy();
//         swiperInstance.navigation.init();
//         swiperInstance.navigation.update();
//     }
// });

watch(
    () => activeTabTrigger,
    () => {
        nextTick(() => {
            const swiper = mySwiper.value.swiper;
            swiper.update();
            swiper.navigation.init();
            swiper.navigation.update();
        });
    }
);

const toggleTabTrigger = (tabIndex) => (activeTabTrigger.value = tabIndex);
</script>

<template>
    <section class="pick" id="pick">
        <div class="container">
            <div class="pick__wrapper">
                <div class="pick__top">
                    <div class="section-title pick__title" v-html="content.title"></div>
                    <div class="pick__subtitle" v-html="content.subtitle"></div>
                </div>

                <div class="pick__bottom">
                    <!-- RENDER TAB TRIGGERS -->
                    <div class="pick__triggers">
                        <button
                            v-for="(item, index) in content.triggers"
                            :key="index"
                            :class="`pick__trigger ${index === activeTabTrigger ? 'active' : ''}`"
                            @click="() => toggleTabTrigger(index)"
                        >
                            {{ item.title }}
                        </button>
                    </div>
                    <div class="pick__contents">
                        <!-- RENDER TABS -->
                        <div
                            v-for="(tabItem, myIndex) in content.tabContents"
                            :key="myIndex"
                            v-show="myIndex === activeTabTrigger"
                            class="pick__content"
                        >
                            <div class="pick__content-pic">
                                <!-- RENDER SLIDES -->
                                <!-- SWIPER -->
                                <swiper
                                    ref="mySwiper"
                                    :modules="[Autoplay, Navigation]"
                                    :autoplay="{ delay: 3000, disableOnInteraction: false }"
                                    :slides-per-view="1"
                                    :loop="true"
                                    :navigation="{
                                        nextEl: '.swiper-button-next',
                                        prevEl: '.swiper-button-prev',
                                    }"
                                    class="mySwiper"
                                >
                                    <swiper-slide v-for="(item, indexx) in tabItem.slidesViews" :key="indexx">
                                        <div class="pick__content-slide">
                                            <div class="pick__content-slide-text">
                                                <span>0{{ indexx + 1 }}.</span>
                                                {{ item.title.toUpperCase() }}
                                            </div>
                                            <div class="pick__content-slide-pic">
                                                <img :src="item.image" alt="trip image" />
                                            </div>
                                        </div>
                                    </swiper-slide>
                                    <!-- SWIPER CUSTOM NAVIGATION ARROWS -->
                                    <div class="custom-nav">
                                        <div class="swiper-button-prev"></div>
                                        <div class="swiper-button-next"></div>
                                    </div>
                                </swiper>
                            </div>
                            <div class="pick__content-body">
                                <div class="pick__content-body-inner">
                                    <div class="pick__content-title" v-html="tabItem.body.title"></div>
                                    <div class="pick__content-text">
                                        <!-- RENDER TEXTS -->
                                        <p
                                            v-for="(itemSocial, indexSocial) in tabItem.body.texts"
                                            :key="indexSocial"
                                            :style="`${
                                                indexSocial === 0
                                                    ? `font-family: 'Larsseit-Bold', sans-serif;`
                                                    : `font-family: 'Larsseit-Regular', sans-serif;`
                                            }`"
                                        >
                                            {{ itemSocial }}
                                        </p>
                                    </div>
                                    <a href="/" class="button pick__content-button">{{ tabItem.body.buttonTitle }}</a>
                                </div>
                                <div class="pick__content-share">
                                    <div class="pick__content-share-text">{{ content.shareBlockText }}</div>
                                    <div class="pick__content-share-icons">
                                        <!-- RENDER SOCIALS -->
                                        <a
                                            v-for="(itemSocial2, indexSocial2) in content.socials"
                                            :key="indexSocial2"
                                            :href="itemSocial2.link"
                                            class="pick__content-share-icon"
                                        >
                                            <img :src="itemSocial2.icon" alt="socials icon" />
                                        </a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<style lang="scss" scoped>
.pick {
    margin-bottom: 300px;
    @media (max-width: #{$md2}) {
        margin-bottom: 70px;
    }

    position: relative;
    &:after {
        content: "";
        position: absolute;
        z-index: -1;
        top: -200px;
        left: 0;
        background: url("@/assets/images/content/bg-lights.png") 0 0 no-repeat;
        background-size: cover;
        width: 100%;
        height: 2963px;
    }

    &__wrapper {
    }

    &__top {
        display: flex;
        align-items: center;
        margin-bottom: 85px;
        @media (max-width: #{$md3}) {
            flex-direction: column;
            align-items: start;
            margin-bottom: 50px;
        }
    }

    &__title {
        font-family: "Noe Display Bold";
        font-weight: 700;
        font-size: 72px;
        letter-spacing: -0.02em;
        margin-right: 90px;
        position: relative;
        &:after {
            content: "";
            position: absolute;
            top: 23px;
            right: -55px;
            background: url("@/assets/images/icons/x.svg") 0 0 no-repeat;
            width: 24px;
            height: 24px;
        }
        @media (max-width: #{$md2}) {
            font-size: 54px;
        }
        @media (max-width: #{$md3}) {
            // margin-right: 0;
            // margin-bottom: 30px;
            margin: 0 auto 30px;
            &:after {
                top: 40px;
            }
        }
        @media (max-width: #{$md4}) {
            // font-size: 52px;
            font-size: 47px;
            &:after {
                display: none;
            }
        }
    }

    &__subtitle {
        font-weight: 400;
        font-size: 18px;
        line-height: 150%;
        // letter-spacing: -0.02em;
        font-family: "Larsseit-Light", sans-serif;
        // font-family: "Larsseit-Regular", sans-serif;
        // max-width: 420px;
        max-width: 300px;
        @media (max-width: #{$md2}) {
            font-size: 16px;
            line-height: 130%;
            max-width: 300px;
        }
        @media (max-width: #{$md3}) {
            max-width: 100%;
            text-align: center;
            margin: 0 auto;
            line-height: 1.5;
        }
    }

    &__bottom {
    }

    &__triggers {
        display: flex;
        justify-content: space-between;
        padding-bottom: 33px;
        margin-bottom: 150px;
        position: relative;
        &:after {
            content: "";
            position: absolute;
            bottom: 0;
            left: 0;
            background-color: rgba($color: $skyblue, $alpha: 0.3);
            width: 100%;
            height: 2px;
            border-radius: 13px;
        }
        @media (max-width: #{$md1}) {
            margin-bottom: 80px;
        }
        @media (max-width: #{$md2}) {
            margin-bottom: 60px;
        }
        @media (max-width: #{$md3}) {
            flex-wrap: wrap;
            padding-bottom: 5px;
        }
    }

    &__trigger {
        flex: 1 1 25%;
        text-align: center;
        // @extend %Larsseit-Bold;
        font-size: 18px;
        letter-spacing: -0.02em;
        color: rgba($color: #fff, $alpha: 0.5);
        background-color: transparent;
        // transition: all 0.2s;
        padding-bottom: 33px;
        &.active {
            color: $skyblue2;
            position: relative;
            &:after {
                content: "";
                position: absolute;
                bottom: -33px;
                left: 0;
                background-color: rgba($color: $skyblue, $alpha: 1);
                width: 100%;
                height: 4px;
                border-radius: 13px;
                @media (max-width: #{$md3}) {
                    bottom: -10px;
                }
            }
        }
        @media (max-width: #{$md3}) {
            flex: 1 1 50%;
            padding-bottom: 0;
            margin-bottom: 33px;
        }
        @media (max-width: #{$md4}) {
            font-size: 15px;
        }
    }

    &__contents {
    }

    &__content {
        // display: none;
        display: flex !important;
        // &.active,
        // &[v-cloak],
        // &[style="display: block"] {
        //     display: flex;
        // }

        &[style="display: none;"] {
            display: none !important;
        }

        @media (max-width: #{$md2}) {
            flex-wrap: wrap;
        }
    }

    &__content-pic {
        flex: 0 1 580px;
        max-height: 607px;
        position: relative;
        // max-width: 486px;
        @media (max-width: 1610px) {
            // margin-left: 95px;
        }
        @media (max-width: #{$md2}) {
            align-self: center;
            flex: 1 1 100%;
            margin-bottom: 70px;
            // order: 2;
        }
        @media (max-width: #{$md3}) {
            flex: 1 1 100%;
            margin-left: 0;
            margin-bottom: 50px;
        }
    }

    &__content-slide {
        position: relative;
        // padding-left: 95px;
        // padding-bottom: 55px;
        @media (max-width: #{$md3}) {
            padding-left: 0;
            padding-bottom: 0;
        }
    }

    &__content-slide-text {
        position: relative;
        position: absolute;
        z-index: 1;
        top: 255px;
        // left: -95px;
        left: 0;
        max-width: 220px;
        font-size: 24px;
        letter-spacing: 0.15em;
        line-height: 150%;

        span {
            display: block;
            // @extend %Larsseit-ExtraBold;
            color: $skyblue2;
            @media (max-width: #{$md3}) {
                margin-bottom: 10px;
            }
        }

        // @extend %Larsseit-Bold;
        &:after {
            content: "";
            position: absolute;
            // top: -9px;
            top: -18px;
            left: 0;
            background: $skyblue2;
            width: 2px;
            height: 12px;
            border-radius: 13px;
        }
        &:before {
            content: "";
            position: absolute;
            // top: -9px;
            top: -18px;
            left: 0;
            background: $skyblue2;
            width: 172px;
            height: 2px;
            border-radius: 13px;
        }

        @media (max-width: #{$md1}) {
            top: 150px;
        }
        @media (max-width: #{$md3}) {
            // top: initial;
            top: 20px;
            // bottom: 20px;
            left: 20px;
            right: 20px;
            background-color: rgba(0, 0, 0, 0.5);
            border-radius: 10px;
            padding: 20px;
            max-width: 100%;
            font-size: 16px;
            &:before,
            &:after {
                display: none;
            }
        }
    }

    &__content-slide-pic {
        // max-width: 486px;
        padding-left: 95px;
        position: relative;
        overflow: hidden;
        // z-index: 1;
        &:after {
            content: "";
            position: absolute;
            z-index: -1;
            // bottom: -55px;
            // left: -55px;
            bottom: -56px;
            left: -19px;
            background: url("@/assets/images/icons/dots2.svg") 0 0 no-repeat;
            width: 230px;
            height: 230px;
            @media (max-width: #{$md2}) {
                // filter: brightness(40%);
                display: none;
            }
        }

        img {
            border-radius: 8px;
            // max-width: 100%;
            width: 100%;
            height: 607px;
            object-fit: cover;
            @media (max-width: #{$md2}) {
                height: 400px;
            }
            @media (max-width: #{$md3}) {
                // height: auto;
                // max-height: 400px;
            }
        }

        @media (max-width: #{$md2}) {
            max-width: 100%;
        }
        @media (max-width: #{$md3}) {
            padding-left: 0;
            &:after {
                display: none;
            }
        }
        // @media (max-width: #{$md4}) {
        //     img {
        //         height: 400px;
        //     }
        // }
    }

    &__content-body {
        flex: 1 1 auto;
        margin-left: 125px;
        display: flex;
        flex-direction: column;
        margin-top: 70px;
        @media (max-width: #{$md1}) {
            margin-top: 0;
            margin-left: 70px;
        }
        @media (max-width: #{$md2}) {
            flex: 1 1 100%;
            // order: 1;
        }
        @media (max-width: #{$md3}) {
            margin-left: 0;
        }
    }

    &__content-body-inner {
        max-width: 485px;
        @media (max-width: #{$md2}) {
            max-width: 100%;
        }
    }

    &__content-title {
        font-family: "Noe Display Bold";
        font-style: normal;
        font-weight: 700;
        font-size: 65px;
        // letter-spacing: -0.02em;
        margin-bottom: 55px;
        @media (max-width: #{$md1}) {
            // font-size: 60px;
            font-size: 52px;
        }
        @media (max-width: #{$md4}) {
            font-size: 45px;
            margin-bottom: 36px;
        }
    }

    &__content-text {
        // @extend %Larsseit-Regular;
        font-size: 17px;
        letter-spacing: -0.02em;

        p {
            line-height: 150%;
        }

        p:nth-child(1) {
            // @extend %Larsseit-Bold;
        }

        p + p {
            margin-top: 30px;
        }

        margin-bottom: 45px;

        @media (max-width: #{$md4}) {
            margin-bottom: 30px;
        }
    }

    &__content-button {
        font-size: 14px;
        margin-bottom: 60px;
        @media (max-width: #{$md2}) {
            margin-bottom: 30px;
        }
        @media (max-width: #{$md4}) {
            display: block;
            text-align: center;
            padding: 20px 58px;
        }
    }

    &__content-share {
        align-self: end;
    }

    &__content-share-text {
        font-size: 15px;
        letter-spacing: 0.15em;
        font-family: "Larsseit-Light", sans-serif;
        margin-bottom: 25px;
        @media (max-width: #{$md3}) {
            margin-bottom: 15px;
        }
    }

    &__content-share-icons {
        display: inline-flex;
        align-items: center;
        column-gap: 30px;
        position: relative;
        &:after {
            content: "";
            position: absolute;
            bottom: -20px;
            left: 0;
            background-color: $skyblue2;
            width: 133px;
            height: 2px;
            border-radius: 13px;
        }
        &:before {
            content: "";
            position: absolute;
            top: 12px;
            right: -12px;
            background-color: $skyblue2;
            width: 2px;
            height: 31px;
            border-radius: 13px;
        }
        @media (max-width: #{$md3}) {
            column-gap: 60px;

            &:after {
                left: -12px;
                bottom: -15px;
                // width: 175px;
                width: 195px;
            }
            &:before {
                right: auto;
                left: -12px;
                top: 7px;
            }
        }
    }

    &__content-share-icon {
        transition: all 0.3s;
        &:hover {
            opacity: 0.5;
        }
    }
}

.mySwiper {
    max-width: 580px;
    @media (max-width: #{$md3}) {
        max-width: 90vw;
    }
}
.swiper {
    position: relative;
}

/* Container for both arrows */
.custom-nav {
    position: absolute;
    bottom: 0;
    right: 0;
    display: flex;
    gap: 5px;
    z-index: 10;
}

/* Arrow button style */
.custom-nav .swiper-button-prev,
.custom-nav .swiper-button-next {
    all: unset;
    background-color: black;
    color: white;
    padding: 20px 30px;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    width: auto;
    height: auto;
    font-size: 16px;
}

.custom-nav .swiper-button-prev:active,
.custom-nav .swiper-button-next:active {
    opacity: 0.7;
}
</style>

<style>
.pick__title span,
.pick__content-title span {
    color: #41ead4;
}
</style>
