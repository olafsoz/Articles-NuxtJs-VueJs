<template>
    <div>
        <header/>
        <articles/>
    </div>
</template>
<script>
import Header from "../layouts/default";
import Articles from "../components/articles"

export default {
    components: {
        'header': Header,
        'articles': Articles
    }
}
</script>

