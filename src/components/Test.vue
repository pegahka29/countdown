<script>

export default {
    //eslint-disable-next-line
    name: "Test",
    data() {
        return {
            countDownToTime: new Date("Jul 18, 2023 00:00:00").getTime(),
            timerOutput: null
        }
    },
    methods: {
        startTimer: function () {
            const timeNow = new Date().getTime();
            const timeDifference = this.countDownToTime - timeNow;
            const millisecondsInOneSecond = 1000;
            const millisecondsInOneMinute = millisecondsInOneSecond * 60;
            const millisecondsInOneHour = millisecondsInOneMinute * 60;
            const millisecondsInOneDay = millisecondsInOneHour * 24;
            const differenceInDays = timeDifference / millisecondsInOneDay;
            const remainderDifferenceInHours = (timeDifference % millisecondsInOneDay) / millisecondsInOneHour;
            const remainderDifferenceInMinutes = (timeDifference % millisecondsInOneHour) / millisecondsInOneMinute;
            const remainderDifferenceInSeconds = (timeDifference % millisecondsInOneMinute) / millisecondsInOneSecond;
            const remainingDays = Math.floor(differenceInDays);
            const remainingHours = Math.floor(remainderDifferenceInHours);
            const remainingMinutes = Math.floor(remainderDifferenceInMinutes);
            const remainingSeconds = Math.floor(remainderDifferenceInSeconds);
            this.timerOutput = remainingDays + " Days " + ": " + remainingHours + " Hours " + ": " + remainingMinutes + " Minutes " + ": " + remainingSeconds + " Seconds";
        }
    },
    mounted() {
        setInterval(() => {
            this.startTimer()
        }, 1000);
    }
}
</script>

<template>
    <div class="v">{{ timerOutput }}
        <h1>{{countDownToTime}} countDownToTime</h1>
    </div>
</template>

<style scoped>

</style>
