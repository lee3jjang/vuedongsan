<template>
    <div>
        <img :src="원룸.image" class="room-img">
        <h4 @click="$emit('openModal')">{{ 원룸.title }}</h4>
        <p>{{ 원룸.price }}원</p>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        원룸: Object,
        모달창열렸니: Boolean,
    }
}
</script>

<style>

</style>