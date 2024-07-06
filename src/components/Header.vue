<template>
    <div>
        <header class="flex flex-col justify-between fixed h-[100vh] font-semibold">
            <div class="logo">
                <img src="../assets/images/logo.png" alt="bakstagetalks" class=" w-[160px] md:w-[260px]">
            </div>
            <div class="description hidden xl:block mb-10 text-[18px] lg:w-[350px]">
                <p>
                    Backstage Talks is a magazine <br>
                    of casual, but in depth dialogues <br>
                    on design and business. Our decisions <br>
                    shape and influence this complex <br>
                    world—to have a chance to make the <br>
                    right ones, we need to talk.
                </p>
            </div>
        </header>
    </div>
</template>
<script>
    export default {
        name: "Header",
    }
</script>