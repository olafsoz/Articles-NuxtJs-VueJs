<template>
    <div>
         <section v-for="(article, index) in articles" :key="index">
             <div v-if="(index + 1) % 2 !== 0">
                <div class="text-center text-6xl text-white font-bold relative text-center flex items-center justify-center">
                    <div class="image"><img :src="article.editorsChoice.thumbnail.sources.landscape.large"></div>
                    <div class="absolute bottom-32 px-12"><a :href="'https://'+info.domain+'/'+article.id">{{ article.headline }}</a></div>
                </div>
                <div class="h-72 flex text-white font-bold">
                    <div class="w-3/4 bg-black h-full flex items-center justify-center">
                        <div v-html="article.articleLead[0].html" class="px-40"></div>
                    </div>
                    <div class="w-1/4 bg-blue-400 h-full flex items-center justify-center">
                        <div class="circle flex items-center justify-center rounded-full w-48 h-48 p-2.5 border-solid border-2 border-white text-center text-3xl">{{ index + 1 }}</div>
                    </div>
                </div>
            </div>
            <div v-else>
                <div class="text-center text-6xl text-white font-bold relative text-center flex items-center justify-center">
                    <div class="image"><img :src="article.editorsChoice.thumbnail.sources.landscape.large"></div>
                    <div class="absolute bottom-32 px-12"><a :href="'https://'+info.domain+'/'+article.id">{{ article.headline }}</a></div>
                </div>
                <div class="h-72 flex text-white font-bold">
                    <div class="w-1/4 bg-blue-400 h-full flex items-center justify-center">
                        <div class="circle flex items-center justify-center rounded-full w-48 h-48 p-2.5 border-solid border-2 border-white text-center text-3xl">{{ index + 1 }}</div>
                    </div>
                    <div class="w-3/4 bg-black h-full flex items-center justify-center">
                        <div v-html="article.articleLead[0].html" class="px-40"></div>
                    </div>
                </div>
            </div>
        </section> 
    </div>
</template>
<script setup>
    const { data: articles } = await useAsyncData('articles', () => $fetch('https://services.postimees.ee/rest/v1/sections/81/editorsChoice/articles?limit=5'))
    const { data: info } = await useAsyncData('info', () => $fetch('https://services.postimees.ee/rest/v1/sections/81'))
</script>
<style>
    .image {
        filter: brightness(40%);
    }
</style>
