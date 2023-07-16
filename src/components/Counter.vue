<template>
    <div>
        <section class="text-3xl flex justify-center flex-col mx-auto text-center"></section>
        <section class="flex text-6xl justify-center content-center">
            <div class="days mr-2 relative">
                {{ displayDays }}
                <div class="label text-sm absolute -bottom-3 ">Days</div>
            </div>
            <span class="landing-snug">
                :
            </span>
            <div class="hours mx-2 relative">
                {{ displayHours }}
                <div class="label text-sm absolute -bottom-3">Hours</div>
            </div>
            <span class="landing-snug">
                :
            </span>
            <div class="minutes mr-2 relative">
                {{ displayMinutes }}
                <div class="label text-sm absolute -bottom-3">Minutes</div>
            </div>
            <span class="landing-snug">
                :
            </span>
            <div class="seconds mr-2 relative">
                {{ displaySeconds }}
                <div class="label text-sm absolute -bottom-3">Seconds</div>
            </div>
        </section>
    </div>
</template>

<script>

export default {
    //eslint-disable-next-line
    name: "Counter",
    data() {
        return {
            displayDays: 0,
            displayHours: 0,
            displayMinutes: 0,
            displaySeconds: 0,
        }
    },
}
</script>


<style scoped>

</style>
