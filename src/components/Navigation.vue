<template>
    <div>
        <div class="flex flex-col justify-between fixed h-[100vh] ml-[-12rem]">
            <div class="email">
                <p><a href="mailto:info@backstagetalks.com" class="font-semibold">info@backstagetalks.com</a></p>
            </div>
            <ul class="mb-10 flex flex-col items-end text-lg text-[#251D20] font-[400]">
                <li v-for="item in listItems" :key="item.number"><a :href="item.href">Issue #{{item.number}}</a></li>
            </ul>
        </div>
    </div>
</template>
<script>
    export default {
       name: "Navigation",
       props: {
        href: String,
       },
       data() {
        return {
            listItems: [
                { number: 8, href: "#" },
                { number: 7, href: "#" },
                { number: 6, href: "#" },
                { number: 5, href: "#" },
                { number: 4, href: "#" },
                { number: 3, href: "#" },
                { number: 2, href: "#" },
                { number: 1, href: "#" },
            ]
        }
       }
    }
</script>