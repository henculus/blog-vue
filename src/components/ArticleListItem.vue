<template>
    <router-link :to="{ name: 'article', params: { id: article.id } }" tag="div" class="list-item">
        <div class="top-image-wrapper">
            <div class="top-image-placeholder"></div>
            <img class="top-image" :src="article.img_src"/>
        </div>
        <div class="article-text-items">
            <div class="title">{{article.title}}</div>
            <div class="subtitle">{{article.subtitle}}</div>
            <!--<div class="article-content"></div>-->
        </div>
    </router-link>
</template>

<script>
    export default {
        name: "ArticleListItem",
        props: {
            article: Object
        },
    }
</script>

<style lang="sass" scoped>
    @import "../variables"
    .list-item
        +deselect
        min-width: 200px
        position: relative
        //box-shadow: 0 0 4px rgba(0, 0, 0, 0.4)
        border: 1px solid $menu_border_color
        margin-bottom: 20px
        display: flex
        flex-direction: column
        cursor: pointer
        background: white
        color: black
        border-radius: $block_border_radius
        font-style: normal
        font-weight: 400
        -webkit-font-smoothing: subpixel-antialiased
        backface-visibility: hidden
        transform: scale(1)
        font-size: 14px
        transition: all 0.15s ease-in-out
        //.top-image-placeholder
            //padding-bottom: 25%

        .top-image-wrapper
            display: none
            position: relative
            overflow: hidden
            border-top-right-radius: $block_border_radius
            border-top-left-radius: $block_border_radius
            max-height: 200px

            .top-image-placeholder
                display: block
                position: relative
                padding-bottom: 25%

            .top-image
                transform: translateZ(0)
                transition: all .2s ease-out
                width: 100%
                position: absolute
                pointer-events: none
                top: 0
                left: 0

        .article-text-items
            padding: 30px

            .title
                font-size: 1.8em
                margin-bottom: 15px
                font-family: $title_font

            .subtitle
                font-size: 1.05em
                font-family: $subtitle_font
                color: $subtitle-color

            .article-content
                position: relative
                font-family: $default_font
    .no-touch .list-item:hover
        border: 1px solid $rnt_green
        box-shadow: 0 0 4px $rnt_green

    +media_screensize_mobile
        .list-item
            font-size: 16px
            .top-image-wrapper
                display: block
        .no-touch .list-item:hover
            border: 1px solid $menu_border_color
            box-shadow: none

    .no-touch
        .list-item:hover
            .top-image
                transform: scale(1.05)


</style>
