<template>
    <div class="container mx-auto px-4" v-if="loaded">
        <div class="flex justify-center items-center bg-white shadow-md rounded pt-6 pb-8 mb-4 h-screen">
            <form>
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2" for="date">
                        Date:
                    </label>
                    <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                           v-model="endTime"
                           id="date" type="datetime-local" placeholder="date">
                </div>
                <section class="text-3xl flex justify-center flex-col mx-auto text-center">
                    <h5 v-if="!expired" class="text-blue-400">Until:
                        {{ endTime }}
                    </h5>
                    <h5 v-else class="text-red-600">Timer is done!</h5>
                </section>
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
                    <div class="seconds mr-2 relative" id="seconds">
                        {{ displaySeconds }}
                        <div class="label text-sm absolute -bottom-3">Seconds</div>
                    </div>
                </section>
            </form>
        </div>
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
            endTime: '',
            loaded: false,
            expired: false
        }
    },
    computed: {
        _seconds: () => 1000,
        _minutes() {
            return this._seconds * 60;
        },
        _hours() {
            return this._minutes * 60;
        },
        _days() {
            return this._hours * 24;
        },
    },
    mounted() {
        this.loaded = true
    },
    watch: {
        endTime(newValue) {
            if (newValue) {
                this.showRemaining()
            }
        }
    },
    methods: {
        formatNum: num => (num < 10 ? '0' + num : num),
        showRemaining() {
            const timer = setInterval(() => {
                const now = new Date()
                const end = new Date(this.endTime)
                const distance = end - now.getTime()
                if (distance < 0) {
                    clearInterval(timer)
                    this.expired = true
                    this.loaded = true
                    return
                }

                const days = Math.floor(distance / this._days);
                const hours = Math.floor((distance % this._days) / this._hours);
                const minutes = Math.floor((distance % this._hours) / this._minutes);
                const seconds = Math.floor((distance % this._minutes) / this._seconds);

                if (seconds < 10 && !this.expired && this.loaded) {
                   document.getElementById('seconds').classList.add('text-red-400')
                }
                this.displaySeconds = this.formatNum(seconds);
                this.displayMinutes = this.formatNum(minutes);
                this.displayHours = this.formatNum(hours);
                this.displayDays = this.formatNum(days);
                this.loaded = true
            }, 1000)
        }
    },
}
</script>

<style scoped>
.seconds {
    max-width: 60px;
}
</style>
