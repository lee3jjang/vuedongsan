<template>

<div class="black-bg">
    <div class="white-bg">
        <img :src="원룸들[누른거].image" style="width:100%">
        <h4>{{ 원룸들[누른거].title }}</h4>
        <p>{{ 원룸들[누른거].content }}</p>
        <input v-model="개월">
        <p>{{ 개월 }} 개월 선택함 : {{ 원룸들[누른거].price*개월 }} 원</p>
        <button @click="$emit('closeModal')">닫기</button>
    </div>
</div>

</template>

<script>
export default {
    name: 'Modal',
    data() {
        return {
            개월: '1',
        }
    },
    // watch: {
    //     개월(after, before) {
    //         if (after<2) {
    //             alert('2개월 이상 입력하셈');
    //             this.개월 = before;
    //         }
    //     }
    // },
    beforeUpdate() {
        if(this.개월 == 2) {
            alert("2개월 이상 입력하셈");
            this.개월
        }
    },
    props: {
        원룸들: Array,
        누른거: Number,
    }
}
</script>

<style>

</style>