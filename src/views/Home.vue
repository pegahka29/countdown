<template>
    <counter
            :minute="0"
            :date="16"
            :hour="17"
            :millisecond="0"
            :month="7"
            :second="0"
            :year="2023"
    />
</template>

<script>

import Counter from "@/components/Counter.vue";

export default {

    //eslint-disable-next-line
    name: "Home",
    components: {Counter}
}
</script>

<style scoped>

</style>
