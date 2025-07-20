<script setup>
const content = {
    title: "<span>P</span>ick <span>Y</span>our <span>T</span>rip",
    subtitle: "Our team put together some trips to you to discover, feel free to discover each of them.",
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
};
</script>

<template>
    <section class="pick" id="pick">
        <div class="container">
            <div class="pick__wrapper">
                <div class="pick__top">
                    <div class="section-title pick__title" v-html="content.title"></div>
                    <div class="pick__subtitle">
                        {{ content.subtitle }}
                    </div>
                </div>
                <div class="pick__bottom">
                    <div class="pick__triggers">
                        <a
                            v-for="(item, index) in content.triggers"
                            :key="index"
                            :href="item.href"
                            :class="`pick__trigger ${index === 0 ? 'active' : ''}`"
                            >{{ item.title }}</a
                        >
                    </div>
                    <div class="pick__contents">
                        <div class="pick__content active" id="chill">
                            <div class="pick__content-pic">
                                <div class="swiper-wrapper">
                                    <div>
                                        <div class="pick__content-slide">
                                            <div class="pick__content-slide-text">
                                                <span>02.</span>
                                                BEAUTIFUL OASIS
                                            </div>
                                            <div class="pick__content-slide-pic">
                                                <img src="images/content/pick-2.jpg" alt="" />
                                            </div>
                                        </div>
                                    </div>
                                    <div
                                        class="swiper-slide swiper-slide-duplicate-active"
                                        data-swiper-slide-index="0"
                                        role="group"
                                        aria-label="1 / 2"
                                        style="width: 490px; margin-right: 110px"
                                    >
                                        <div class="pick__content-slide">
                                            <div class="pick__content-slide-text">
                                                <span>01.</span>
                                                GRAND DUNES LANDSCAPE
                                            </div>
                                            <div class="pick__content-slide-pic">
                                                <img src="images/content/pick-1.jpg" alt="" />
                                            </div>
                                        </div>
                                    </div>
                                    <div
                                        class="swiper-slide swiper-slide-prev swiper-slide-duplicate-next"
                                        data-swiper-slide-index="1"
                                        role="group"
                                        aria-label="2 / 2"
                                        style="width: 490px; margin-right: 110px"
                                    >
                                        <div class="pick__content-slide">
                                            <div class="pick__content-slide-text">
                                                <span>02.</span>
                                                BEAUTIFUL OASIS
                                            </div>
                                            <div class="pick__content-slide-pic">
                                                <img src="images/content/pick-2.jpg" alt="" />
                                            </div>
                                        </div>
                                    </div>
                                    <div
                                        class="swiper-slide swiper-slide-duplicate swiper-slide-active"
                                        data-swiper-slide-index="0"
                                        role="group"
                                        aria-label="1 / 2"
                                        style="width: 490px; margin-right: 110px"
                                    >
                                        <div class="pick__content-slide">
                                            <div class="pick__content-slide-text">
                                                <span>01.</span>
                                                GRAND DUNES LANDSCAPE
                                            </div>
                                            <div class="pick__content-slide-pic">
                                                <img src="images/content/pick-1.jpg" alt="" />
                                            </div>
                                        </div>
                                    </div>
                                </div>
                                <div
                                    class="swiper-button-prev"
                                    tabindex="0"
                                    role="button"
                                    aria-label="Previous slide"
                                    aria-controls="swiper-wrapper-10602b1079631987b2"
                                ></div>
                                <div
                                    class="swiper-button-next"
                                    tabindex="0"
                                    role="button"
                                    aria-label="Next slide"
                                    aria-controls="swiper-wrapper-10602b1079631987b2"
                                ></div>
                                <span class="swiper-notification" aria-live="assertive" aria-atomic="true"></span>
                            </div>
                            <div class="pick__content-body">
                                <div class="pick__content-body-inner">
                                    <div class="pick__content-title">Chill Adventure</div>
                                    <div class="pick__content-text">
                                        <p>
                                            Ornare vivamus molestie pellentesque nunc. Sed sapien erat ultrices curabitur. Erat id
                                            fringilla arcu condimentum fames.
                                        </p>
                                        <p>
                                            Aliquet dictum aliquet faucibus cursus turpis. Suspendisse cum rutrum sit ut sociis.
                                            Pellentesque neque orci adipiscing pharetra lacus, dignissim pharetra ipsum blandit.
                                            Feugiat quis quam consectetur lectus id quis tortor vel, mattis.
                                        </p>
                                    </div>
                                    <a href="#" class="button pick__content-button">SEE OUR LATEST OFFER</a>
                                </div>
                                <div class="pick__content-share">
                                    <div class="pick__content-share-text">SHARE IT:</div>
                                    <div class="pick__content-share-icons">
                                        <a href="#" class="pick__content-share-icon">
                                            <img src="images/icons/ig.svg" alt="" />
                                        </a>
                                        <a href="#" class="pick__content-share-icon">
                                            <img src="images/icons/fb.svg" alt="" />
                                        </a>
                                        <a href="#" class="pick__content-share-icon">
                                            <img src="images/icons/twi.svg" alt="" />
                                        </a>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- -->
                        <div class="pick__content" id="spooky">
                            <div class="pick__content-text">
                                <p>
                                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolore officia assumenda impedit
                                    dicta facilis rerum, laudantium quibusdam harum ullam laboriosam ipsa ducimus soluta,
                                    asperiores doloribus rem atque odio non distinctio, vero dolores incidunt quaerat ratione
                                    doloremque. Iste, delectus? Quos animi, soluta nam officia quaerat iste optio veritatis
                                    aspernatur praesentium sunt beatae, repudiandae nulla, eum iusto tempore dolore.
                                </p>
                                <p>
                                    Vel accusamus quaerat eligendi quae iste quos, ducimus commodi iusto optio. Non, repellat
                                    debitis aperiam quis excepturi nostrum quod delectus expedita culpa quam obcaecati amet beatae
                                    facere adipisci quasi sed? Amet doloribus quas corrupti! Enim consequatur consequuntur quos
                                    consectetur quis inventore eius ratione!
                                </p>
                                <p>
                                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolore officia assumenda impedit
                                    dicta facilis rerum, laudantium quibusdam harum ullam laboriosam ipsa ducimus soluta,
                                    asperiores doloribus rem atque odio non distinctio, vero dolores incidunt quaerat ratione
                                    doloremque. Iste, delectus? Quos animi, soluta nam officia quaerat iste optio veritatis
                                    aspernatur praesentium sunt beatae, repudiandae nulla, eum iusto tempore dolore.
                                </p>
                                <p>
                                    Vel accusamus quaerat eligendi quae iste quos, ducimus commodi iusto optio. Non, repellat
                                    debitis aperiam quis excepturi nostrum quod delectus expedita culpa quam obcaecati amet beatae
                                    facere adipisci quasi sed? Amet doloribus quas corrupti! Enim consequatur consequuntur quos
                                    consectetur quis inventore eius ratione!
                                </p>
                                <p>
                                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolore officia assumenda impedit
                                    dicta facilis rerum, laudantium quibusdam harum ullam laboriosam ipsa ducimus soluta,
                                    asperiores doloribus rem atque odio non distinctio, vero dolores incidunt quaerat ratione
                                    doloremque. Iste, delectus? Quos animi, soluta nam officia quaerat iste optio veritatis
                                    aspernatur praesentium sunt beatae, repudiandae nulla, eum iusto tempore dolore.
                                </p>
                                <p>
                                    Vel accusamus quaerat eligendi quae iste quos, ducimus commodi iusto optio. Non, repellat
                                    debitis aperiam quis excepturi nostrum quod delectus expedita culpa quam obcaecati amet beatae
                                    facere adipisci quasi sed? Amet doloribus quas corrupti! Enim consequatur consequuntur quos
                                    consectetur quis inventore eius ratione!
                                </p>
                            </div>
                        </div>

                        <!-- -->
                        <div class="pick__content" id="desert">
                            <div class="pick__content-text">
                                <p>
                                    Lorem ipsum dolor sit amet consectetur, adipisicing elit. Obcaecati quasi, totam omnis
                                    cupiditate, deserunt cumque natus autem tempora nam aliquid repudiandae eligendi
                                    exercitationem officiis corrupti magni maiores animi?
                                </p>
                                <p>
                                    Neque architecto temporibus nisi magnam quam obcaecati! Consectetur nemo cumque reprehenderit,
                                    laudantium modi illo soluta amet delectus magni, rerum laborum dolorum deserunt placeat,
                                    minima quisquam. Vitae aliquam totam molestiae ducimus illum enim est dolores nobis quis
                                    similique repellendus adipisci, esse, voluptatem nisi consequuntur sequi voluptas soluta, et
                                    ea incidunt temporibus! Corrupti, dolorem illum? Est illo voluptas aperiam consequuntur quidem
                                    consequatur repudiandae eius amet alias fuga deserunt vero aliquid, soluta nihil, voluptatum
                                    veritatis natus odio voluptate, impedit cupiditate quis.
                                </p>
                                <p>
                                    Excepturi voluptates, illum nesciunt blanditiis accusantium at iste. Facere nisi magni quos
                                    assumenda itaque, in libero, culpa laborum est molestias mollitia, soluta nam odio quis non
                                    minima earum odit? Voluptas, iusto dolor vitae veritatis temporibus blanditiis dolorem
                                    consequuntur suscipit eos explicabo debitis fugiat perferendis cum facere. Cum recusandae
                                    quibusdam harum quod sit ex iure laboriosam totam. Recusandae nulla possimus perferendis
                                    labore id incidunt, sint voluptatem illum explicabo inventore eius perspiciatis dolorem velit
                                    maiores neque quidem sed dolor, debitis, rerum quibusdam!
                                </p>
                                <p>
                                    Sit at doloribus eligendi impedit qui quos officiis iure labore quod hic! Doloribus, voluptas.
                                </p>
                            </div>
                        </div>

                        <!-- -->
                        <div class="pick__content" id="wild">
                            <div class="pick__content-text">
                                <p>
                                    Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quod at praesentium, rerum qui
                                    voluptates voluptas id totam similique molestias, quisquam assumenda doloribus expedita labore
                                    sit dignissimos cumque aspernatur ea temporibus non cum quae. Corrupti nemo libero placeat
                                    nihil tempore sapiente iusto cupiditate, unde voluptas doloribus quae ipsum obcaecati eum
                                    architecto, ea eius consequatur molestias enim praesentium.
                                </p>
                                <p>
                                    Autem, iste cum! Minima molestias, aut consequuntur veritatis fugit, dignissimos deleniti
                                    reprehenderit vel voluptatum rerum harum voluptatem dolorum ut ratione expedita repudiandae
                                    consectetur natus eos vero minus ipsum temporibus? Asperiores expedita facilis qui
                                    voluptatibus soluta corrupti velit doloremque possimus quasi, id placeat officia quidem harum
                                    quaerat amet nostrum obcaecati unde incidunt, et ullam repellendus doloribus reiciendis.
                                </p>
                                <p>
                                    Doloremque corporis deleniti reprehenderit, perspiciatis vero ea earum ducimus debitis
                                    inventore reiciendis necessitatibus porro amet hic. Dolor praesentium officiis alias nostrum
                                    nam! Corporis explicabo, maxime laborum rerum suscipit nisi maiores eos magnam sed? Iusto aut
                                    architecto cupiditate reiciendis ea alias quo nesciunt eligendi eos atque similique,
                                    reprehenderit expedita modi deserunt laborum doloribus aspernatur numquam quas debitis. Vitae
                                    distinctio molestiae assumenda velit doloremque unde, ea laboriosam omnis voluptate
                                    voluptatem. Quos enim commodi ea atque fugiat non in modi quis iusto est deleniti
                                    necessitatibus aperiam, voluptates numquam dignissimos pariatur aspernatur, quasi praesentium
                                    perspiciatis reprehenderit? Consectetur delectus voluptatibus enim ipsam nulla assumenda
                                    molestias quibusdam rem laboriosam ad commodi doloribus earum itaque iure neque facilis, dolor
                                    voluptate architecto eius, blanditiis debitis illum officiis vitae nisi. Natus tempore, fugit
                                    neque ratione sit eveniet numquam modi aliquid quos omnis ex.
                                </p>
                                <p>
                                    Explicabo magni pariatur sunt distinctio quibusdam animi ex nesciunt tempore quas nemo
                                    voluptate assumenda praesentium maiores natus sequi aspernatur deleniti sapiente sed, omnis
                                    asperiores, beatae reprehenderit odio laudantium consequatur. Optio aut repellat cumque
                                    maxime, vero eum, rerum cum dolores saepe hic labore esse in autem asperiores cupiditate.
                                    Dolorem eum vitae adipisci, eligendi obcaecati sapiente.
                                </p>
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
        background: url("../images/content/bg-lights.png") 0 0 no-repeat;
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
            background: url("../images/icons/x.svg") 0 0 no-repeat;
            width: 24px;
            height: 24px;
        }
        @media (max-width: #{$md2}) {
            font-size: 54px;
        }
        @media (max-width: #{$md3}) {
            margin-right: 0;
            margin-bottom: 30px;
            &:after {
                top: 60px;
            }
        }
        @media (max-width: #{$md4}) {
            font-size: 52px;
            &:after {
                display: none;
            }
        }
    }

    &__subtitle {
        font-weight: 400;
        font-size: 16px;
        line-height: 150%;
        letter-spacing: -0.02em;
        max-width: 350px;
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
        display: none;
        &.active {
            display: flex;
        }
        @media (max-width: #{$md2}) {
            flex-wrap: wrap;
        }
    }

    &__content-pic {
        flex: 0 1 580px;
        // max-width: 486px;
        @media (max-width: 1610px) {
            margin-left: 95px;
        }
        @media (max-width: #{$md2}) {
            align-self: center;
            flex: 1 1 100%;
            margin-bottom: 100px;
            // order: 2;
        }
    }

    &__content-slide {
        position: relative;
    }

    &__content-slide-text {
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
        }
        // @extend %Larsseit-Bold;
        &:after {
            content: "";
            position: absolute;
            top: -9px;
            left: 0;
            background: $skyblue2;
            width: 2px;
            height: 12px;
            border-radius: 13px;
        }
        &:before {
            content: "";
            position: absolute;
            top: -9px;
            left: 0;
            background: $skyblue2;
            width: 172px;
            height: 2px;
            border-radius: 13px;
        }
        @media (max-width: #{$md1}) {
            top: 150px;
        }
        @media (max-width: #{$md4}) {
            top: 75px;
        }
    }

    &__content-slide-pic {
        max-width: 486px;
        position: relative;
        // z-index: 1;
        &:after {
            content: "";
            position: absolute;
            z-index: -1;
            bottom: -55px;
            left: -55px;
            background: url("../images/icons/dots2.svg") 0 0 no-repeat;
            width: 230px;
            height: 230px;
        }
        img {
            border-radius: 8px;
            max-width: 100%;
            width: 100%;
            height: 607px;
            object-fit: cover;
        }
        @media (max-width: #{$md2}) {
            max-width: 100%;
        }
        @media (max-width: #{$md4}) {
            img {
                height: 400px;
            }
        }
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
    }

    &__content-title {
        font-family: "Noe Display Bold";
        font-style: normal;
        font-weight: 700;
        font-size: 65px;
        letter-spacing: -0.02em;
        margin-bottom: 55px;
        @media (max-width: #{$md1}) {
            font-size: 60px;
        }
        @media (max-width: #{$md4}) {
            font-size: 45px;
            margin-bottom: 36px;
        }
    }

    &__content-text {
        // @extend %Larsseit-Regular;
        font-size: 17px;
        line-height: 150%;
        letter-spacing: -0.02em;
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
    }

    &__content-share {
        align-self: end;
    }

    &__content-share-text {
        font-size: 15px;
        letter-spacing: 0.15em;
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
            &:after {
                left: -12px;
                bottom: -15px;
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
</style>
