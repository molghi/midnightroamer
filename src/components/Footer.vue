<script setup>
import { ref } from "vue";
import twiImg from "@/assets/images/icons/twi.svg";
import igImg from "@/assets/images/icons/ig.svg";
import fbImg from "@/assets/images/icons/fb.svg";

const content = {
    site: "MR",
    columns: [
        {
            title: "About",
            items: [
                { title: "Our Mission", link: "/" },
                { title: "Terms", link: "/" },
                { title: "Copyright", link: "/" },
            ],
        },
        {
            title: "FAQ",
            items: [
                { title: "Rules", link: "/" },
                { title: "Tickets", link: "/" },
                { title: "Editions", link: "/" },
                { title: "Contribute", link: "/" },
            ],
        },
        {
            title: "Events",
            items: [
                { title: "Star Gazing", link: "/" },
                { title: "Desert Mania", link: "/" },
                { title: "Dunes Madness", link: "/" },
                { title: "Spooky Land", link: "/" },
            ],
        },
        {
            title: "Contact Us",
            items: [
                { title: "hello@example.com", link: "mailto:hello@example.com" },
                { title: "(405) 555-0128", link: "tel:+4055550128" },
                { title: "(252) 555-0126", link: "tel:+2525550126" },
            ],
        },
        {
            title: "Follow Us",
            items: [
                { link: "/", icon: twiImg },
                { link: "/", icon: igImg },
                { link: "/", icon: fbImg },
            ],
        },
    ],
};

const activeColumn = ref(content.columns.length - 1);

const toggleColumn = (clickedCol) => (activeColumn.value = clickedCol);

const goToTop = () => document.body.scrollTo({ top: 0, behavior: "smooth" });
</script>

<template>
    <footer class="footer">
        <div class="container">
            <div class="footer__wrapper">
                <div class="footer__top">
                    <div v-for="(item, index) in content.columns" :key="index" class="footer__column">
                        <div
                            :class="`footer__column-title ${activeColumn === index ? 'active' : ''}`"
                            @click="() => toggleColumn(index)"
                        >
                            {{ item.title }}
                        </div>

                        <!-- RENDER COLUMNS -->
                        <ul
                            v-if="index !== content.columns.length - 1"
                            :class="`footer__list ${activeColumn === index ? 'expanded' : ''}`"
                        >
                            <li v-for="(element, index) in item.items" :key="index" class="footer__item">
                                <a :href="element.link" class="footer__link">{{ element.title }}</a>
                            </li>
                        </ul>

                        <!-- RENDER SOCIALS COLUMN -->
                        <div v-else :class="`footer__social ${activeColumn === index ? 'expanded' : ''}`">
                            <div class="footer__social-inner">
                                <a v-for="(el, index) in item.items" :key="index" :href="el.link" class="footer__social-link">
                                    <img :src="el.icon" alt="socials icon" />
                                </a>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="footer__bottom">
                    <div class="footer__copyright">Copyright © Midnight Roamer 2025. All rights reserved.</div>
                    <button class="footer__logo logo" @click="goToTop">{{ content.site }}<span>.</span></button>
                </div>
            </div>
        </div>
    </footer>
</template>

<style lang="scss" scoped>
.footer {
    background-color: #011627;
    color: #fff;
    padding: 100px 170px 170px;

    @media (max-width: #{$md1}) {
        padding: 100px 0 170px;
    }
    @media (max-width: #{$md3}) {
        padding: 50px 0;
    }
    @media (max-width: #{$md4}) {
        padding: 30px 0;
    }

    &__wrapper {
    }

    &__top {
        display: flex;
        justify-content: space-between;
        margin-bottom: 75px;
        @media (max-width: #{$md2}) {
            column-gap: 30px;
        }
        @media (max-width: #{$md3}) {
            flex-direction: column;
            margin-bottom: 20px;
        }
    }

    &__column {
        @media (max-width: #{$md3}) {
            margin: 0 auto;
            min-width: 200px;
        }
    }

    &__column-title {
        // @extend %Larsseit-Bold;
        pointer-events: none;
        font-size: 18px;
        line-height: 24px;
        text-transform: uppercase;
        padding-bottom: 23px;
        margin-bottom: 18px;

        @media (max-width: #{$md3}) {
            pointer-events: all;
            display: inline-block;
            width: 250px;
            margin: 0 auto 18px;
            padding-bottom: 0;
            position: relative;
            &:after {
                content: "〉";
                transform: rotate(90deg);
                position: absolute;
                top: 9px;
                right: 0;
                width: 0px;
                height: 0px;
                pointer-events: none;
            }
            &.active {
                &:after {
                    top: 14px;
                    // right: 21px;
                    right: 18px;
                    transform: rotate(-90deg);
                }
            }
        }
    }

    &__list {
        position: relative;
        &:after {
            content: "";
            position: absolute;
            top: -25px;
            left: 0;
            background: url("@/assets/images/icons/divider.svg") 0 0 no-repeat;
            background-size: contain;
            width: 60px;
            height: 11px;
        }
        &.expanded {
            display: block;
            padding-left: 15px;
        }
        @media (max-width: #{$md3}) {
            display: none;
            min-width: 200px;
            margin-bottom: 20px;
            margin-top: 23px;
        }
    }

    &__item {
        font-family: "Larsseit-Light", sans-serif;
        &:hover {
            text-decoration: underline;
        }

        & + & {
            margin-top: 29px;
        }
        @media (max-width: #{$md3}) {
            & + & {
                margin-top: 15px;
            }
        }
    }

    &__link {
        // @include hover-underline;
        @media (max-width: #{$md3}) {
            font-size: 15px;
        }
    }

    &__social {
        position: relative;
        &:after {
            content: "";
            position: absolute;
            top: -25px;
            left: 0;
            background: url("@/assets/images/icons/divider.svg") 0 0 no-repeat;
            background-size: contain;
            width: 60px;
            height: 11px;
        }
        &.expanded {
            display: block;
        }

        @media (max-width: #{$md3}) {
            display: none;
            min-width: 200px;
            margin-bottom: 20px;
            margin-top: 23px;
        }
    }

    &__social-inner {
        display: flex;
        align-items: center;
        column-gap: 25px;
    }

    &__social-link {
        transition: all 0.3s;
        &:hover {
            opacity: 0.5;
        }
    }

    &__bottom {
        text-align: center;
    }

    &__copyright {
        font-size: 15px;
        margin-bottom: 50px;
        font-family: "Larsseit-Light", sans-serif;

        @media (max-width: #{$md3}) {
            margin-bottom: 30px;
        }
        @media (max-width: #{$md4}) {
            font-size: 12px;
        }
    }

    &__logo {
        background-color: transparent;
        color: white;
        &:active {
            opacity: 0.4;
        }
    }
}
</style>
