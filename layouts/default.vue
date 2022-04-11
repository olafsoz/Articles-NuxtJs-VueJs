<template>
    <div class="bg-gray-100 min-h-screen">
        <Title>Articles</Title>
        <nav class="bg-blue-400 shadow text-lg px-6 py-6">
            <div class="container mx-auto flex items-center justify-between px-6">
                <div>
                    <a :href="'https://'+info2.domain"><img src="logo.png" alt="logo"></a>
                </div>
                <div class="text-xs px-4">
                    <p>Aliquam at congue nulla, nunc scelerisque feugiat nibh vel suscipit</p>
                </div>
                <div class="inline">
                    <ul class="flex space-x-4">
                        <li><img src="Facebook.png" alt="facebook"></li>
                        <li><img src="Twitter.png" alt="twitter"></li>
                        <li><img src="Email.png" alt="email"></li>
                    </ul>
                </div>
            </div>
        </nav>
        <slot />
    </div>
</template>
<script setup>
// const info = ref([])

// onMounted(() => {
//     fetch('https://services.postimees.ee/rest/v1/sections/81')
//     .then(response => response.json())
//     .then(data => info.value = data)
// })

const { data: info2 } = await useAsyncData('info2', () => $fetch('https://services.postimees.ee/rest/v1/sections/81'))
</script>

<style scoped>
    nav {
        color: white;
    }
</style>