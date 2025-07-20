<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
import searchImg from "@/assets/images/icons/searchy.svg";

const content = {
    site: "MR",
    menuTitle: "Menu",
    searchPlaceholder: "Search",
    searchIcon: searchImg,
    menuItems: [
        { title: "Pick Your Trip", link: "#pick" },
        { title: "About Us", link: "#about" },
        { title: `People's Thoughts`, link: "#thoughts" },
    ],
};

const targetRef = ref(null); // Reference to the DOM element to watch

const isSearchActive = ref(false);
const searchRef = ref(null);
const isMenuActive = ref(false);

const toggleSearch = () => {
    isSearchActive.value = !isSearchActive.value;
    searchRef.value?.focus();
};

const toggleMenu = () => {
    isMenuActive.value = !isMenuActive.value;
};

const hideMenu = () => {
    isMenuActive.value = false;
    isSearchActive.value = false;
};

// Function to run when click is outside
function handleClickOutside(event) {
    if (targetRef.value && !targetRef.value.contains(event.target)) {
        // Do when clicked outside the element
        hideMenu();
    }
}

// Attach event listener on mount
onMounted(() => document.addEventListener("click", handleClickOutside));

// Remove event listener on unmount to avoid memory leaks
onBeforeUnmount(() => document.removeEventListener("click", handleClickOutside));
</script>

<template>
    <header class="header">
        <div class="container">
            <div class="header__wrapper">
                <!-- LOGO -->
                <a href="/" class="header__logo logo">
                    {{ content.site }}<span>.</span>
                    <!-- <img src="@/assets/images/icons/logo.svg" alt="" /> -->
                </a>

                <div ref="targetRef" class="header__box">
                    <div class="header__search">
                        <!-- SEARCH ICON -->
                        <button class="header__searchy" @click="toggleSearch">
                            <img :src="content.searchIcon" alt="search icon" />
                        </button>

                        <!-- SEARCH FORM -->
                        <form class="header__search-form">
                            <div class="header__search-input-box">
                                <input
                                    ref="searchRef"
                                    type="text"
                                    :class="`header__search-input ${isSearchActive ? 'active' : ''}`"
                                    :placeholder="content.searchPlaceholder"
                                />
                            </div>
                        </form>
                    </div>

                    <!-- MENU -->
                    <div class="header__menu-box">
                        <button class="header__button button" @click="toggleMenu">{{ content.menuTitle }}</button>
                        <nav :class="`header__menu ${isMenuActive ? 'active' : ''}`">
                            <ul class="header__list">
                                <li
                                    v-for="(item, index) in content.menuItems"
                                    :key="index"
                                    class="header__list-item"
                                    @click="hideMenu"
                                >
                                    <a :href="item.link" class="header__link">{{ item.title }}</a>
                                </li>
                            </ul>
                        </nav>
                    </div>
                </div>
            </div>
        </div>
    </header>
</template>

<style lang="scss" scoped>
.header {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 100;
    padding: 50px 0;

    @media (max-width: #{$md4}) {
        padding: 20px 0;
    }

    &__wrapper {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    &__logo {
    }

    &__box {
        display: flex;
        align-items: center;
    }

    &__search {
        display: flex;
        @media (max-width: #{$md3}) {
            // position: relative;
        }
    }

    &__searchy {
        background-color: transparent;
        transition: all 0.3s;
        &:hover {
            opacity: 0.6;
        }
        &:active {
            opacity: 0.4;
        }
    }

    &__search-form {
        margin-left: 15px;
        @media (max-width: #{$md3}) {
            position: absolute;
            // top: 300%;
            top: 130px;
            // right: -200px;
            min-width: 300px;
            right: 10px;
        }
        @media (max-height: 650px) {
            top: 230%;
        }
        @media (max-width: #{$md4}) {
            // top: 250%;
            top: 80px;
            // right: -132px;
        }
    }

    &__search-input-box {
    }

    &__search-input {
        padding: 0 0 8px;
        background-color: transparent;
        border-bottom: 1px solid #fff;
        color: #fff;
        width: 0;
        transition: all 0.3s;

        &::placeholder {
            color: rgba(#fff, 0.4);
        }

        &.active {
            padding: 0 5px 8px;
            width: 300px;
        }

        @media (max-width: #{$md3}) {
            width: 300px;
            opacity: 0;
            visibility: hidden;
            transform: translateY(-30px);
            &.active {
                width: 100%;
                opacity: 1;
                visibility: visible;
                transform: translateY(0);
            }
        }
    }

    &__button {
        margin-left: 34px;

        &:active {
            opacity: 0.5;
        }

        @media (max-width: #{$md4}) {
            margin-left: 25px;
        }
    }

    &__menu-box {
        position: relative;
    }

    &__menu {
        color: #fff;
        position: absolute;
        top: 150%;
        left: 1000%;
        width: 200px;
        transition: all 0.3s;

        &.active {
            left: 10px;

            @media (max-width: #{$md1}) {
                top: 135%;
            }
            @media (max-width: #{$md2}) {
                top: 120%;
                left: 20px;
            }
            @media (max-width: #{$md3}) {
                top: 120%;
                width: 180px;
                left: 60px;
            }
            @media (max-width: #{$md4}) {
                top: 140%;
                left: -10px;
            }
            @media (max-width: #{$md2}) and (max-height: 650px) {
                background-color: rgba($color: #38285c, $alpha: 1);
                min-width: 220px;
                padding: 20px;
                border-radius: 10px;
                box-shadow: 0 0 8px 8px #38285c;
                left: -20px;
                top: 130%;
            }
            @media (max-width: #{$md3}) and (max-height: 650px) {
                min-width: 190px;
                left: 5px;
            }
            @media (max-width: #{$md4}) and (max-height: 650px) {
                left: -60px;
            }
        }
    }

    &__list {
    }

    &__list-item {
        & + & {
            margin-top: 20px;
        }

        @media (max-width: #{$md1}) {
            & + & {
                margin-top: 15px;
            }
        }
        @media (max-width: #{$md2}) {
            & + & {
                margin-top: 13px;
            }
        }
        // @media (max-width: $md3+px){
        //     &+& {margin-top: 13px;}
        // }
        @media (max-width: #{$md4}) {
            & + & {
                margin-top: 12px;
            }
        }
    }

    &__link {
        font-size: 22px;
        font-weight: 600;
        padding-bottom: 3px;
        border-bottom: 1px solid transparent;
        transition: all 0.3s;

        &:hover {
            color: $skyblue;
            border-color: $skyblue;
        }
        @media (max-width: #{$md2}) {
            font-size: 20px;
        }
        @media (max-width: #{$md3}) {
            font-size: 16px;
        }
    }
}
</style>
