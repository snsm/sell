<template>
    <div class="star" :class="starType">
        <span v-for="itemClass in itemClasses" :class="itemClass" class="star-item"></span>
    </div>
</template>

<script>
    export default{
        props: {
            size: {
                type: Number
            },
            score: {
                type: Number
            },
        },
        computed: {
            starType(){
                return 'star-' + this.size;
            }
        },
    }
</script>

<style>
    .star{
        font-size: 0;
    }
    star-item{
        display: inline-block;
        background-repeat: no-repeat;
    }
    .star.star-48 .star-item.on {
    background-image: url("star24_half@2x.png");
}
    .star.star-48 .star-item {
        width: 20px;
        height: 20px;
        margin-right: 22px;
        background-size: 20px 20px;
}
.star .star-item {
    display: inline-block;
    background-repeat: no-repeat;
}
</style>
