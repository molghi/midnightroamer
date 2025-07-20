<script setup>
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
                "Elementum mi felis, sit velit lobortis ultricies non. Mattis enim, nisl",
                "Adipiscing natoque diam et. Cum posuere in velit massa sagittis augue egestas. Eu sollicitudin et quam eu. Nunc, sed imperdiet blandit morbi. Maecenas lobortis tristique rutrum.",
            ],
            name: "Judy ROSELESS",
            position: "MARKETING HEAD at rom",
            image: person1,
        },
        {
            paragraphs: [
                "Lorem ipsum dolor sit amet consectetur adipisicing elit. Qui eaque optio cupiditate",
                "Saborum ipsum dolor sit amet consectetur adipisicing elit. Inventore debitis placeat rem deleniti reprehenderit laborum.",
            ],
            name: "Daisy Clough",
            position: "Product Manager at rom",
            image: person2,
        },
        {
            paragraphs: [
                "Lorem ipsum dolor sit amet consectetur adipisicing elit. Omnis, quod animi",
                "Vero ipsum dolor, sit amet consectetur adipisicing elit. Non, aspernatur quae porro, reiciendis quam, vel numquam minus vero illo?",
            ],
            name: "Karen McDonald",
            position: "Regional Head at rom",
            image: person3,
        },
        {
            paragraphs: [
                "Lorem ipsum dolor sit, amet consectetur adipisicing elit. Nam, quae",
                "Legendi ipsum, dolor sit amet consectetur adipisicing elit. Obcaecati, recusandae placeat! Earum eligendi, id itaque aliquam illo molestias beatae a nostrum nobis aspernatur!",
            ],
            name: "Matt Uvaldi",
            position: "SEO manager at rom",
            image: person4,
        },
    ],
};
</script>

<template>
    <section class="thoughts" id="thoughts">
        <div class="another-container">
            <div class="thoughts__wrapper">
                <div class="section-title thoughts__title" v-html="content.title"></div>
                <div class="thoughts__subtitle">{{ content.subtitle }}</div>
                <div class="thoughts__items">
                    <div v-for="(item, index) in content.testimonials" :key="index" class="thoughts__item">
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

<style>
.thoughts__title span {
    color: #00c9e0;
}
</style>
