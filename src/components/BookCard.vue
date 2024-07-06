<template>
    <section class="h-[100vh] flex flex-col items-center justify-center text-center font-semibold text-[15px]">
        <img :src='image' :alt='alt' class="w-[80%] lg:w-[auto] max-w-[420px]">
        <div class="issue mb-4">
            Issue #{{ issue }} 
            <span class="sold-out" :class="[sold ? 'inline-block' : 'hidden']">
                is sold out
            </span>
        </div>

        <div class="buy" :class="[sold ? 'hidden' : 'block']">
            <a href="#" :class="[issue == 7 ? 'hidden' : 'block', issue == 6 ? 'text-[#FF608B]' : 'text-white']">BUY HERE</a>
            <div :class="[issue == 7 ? 'block' : 'hidden' ]" class="text-white">
                <a href="#">BUY HERE <span class="text-black">(Europe)</span></a> <br>
                <a href="#">BUY HERE <span class="text-black">(UK & Overseas)</span></a>
            </div>
            
            <p class="mt-4">or in 
                <a href="#" :class="[issue == 6 ? 'text-[#FF608B]' : 'text-white']">
                selected stores
                </a>
            </p>
        </div>
        <div class="sold-out" :class="[sold ? 'block' : 'hidden']">
            <p class="mt-4">
                if you are lucky, you may get the last pieces in 
                <a href="#" class="text-white">
                    selected stores
                </a>
            </p>
        </div>
    </section>
</template>
<script>
    export default {
        name: "BookCard",
        props: {
            image: String,
            alt: String,
            issue: Number,
            sold: Boolean,
        }
    }
</script>