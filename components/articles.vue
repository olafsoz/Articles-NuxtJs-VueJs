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
                        <div class="circle flex items-center justify-center">{{ index + 1 }}</div>
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
                        <div class="circle flex items-center justify-center">{{ index + 1 }}</div>
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
    /* .image {
        background-image: -moz-linear-gradient(0deg, rgb(0, 0, 0) 0%, rgba(0, 0, 0, 0.18039) 100%);
        background-image: -webkit-linear-gradient(0deg, rgb(0, 0, 0) 0%, rgba(0, 0, 0, 0.18039) 100%);
        background-image: -ms-linear-gradient(0deg, rgb(0, 0, 0) 0%, rgba(0, 0, 0, 0.18039) 100%);
    } */
    .circle {
        border-radius: 50%;
        width: 120px;
        height: 120px;
        padding: 10px;
        border: 2px solid #ffffff;
        text-align: center;
        font: 32px Arial, sans-serif;
      }
</style>
