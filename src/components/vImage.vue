<template>
    <div class="image">
        
        <img :src="'../assets/BEARD' + image + '.png'" alt="">
    </div>
</template>

<script>

export default ({
    props: {
        image: String
    }
})
</script>

<style scoped>
.image {
    width: 30px;
    height: 30px;
}
</style>