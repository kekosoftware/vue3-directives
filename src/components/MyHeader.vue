<template>
    <div class="row">
        <div class="col-12 col-md-6">
            <h1>Formularios</h1>
        </div>
        <div class="col-12 col-md-6">
            <img width="50px" :src="url" alt="">
        </div>
    </div>
</template>

<script>
    export default {
        data: () => ({
            url: "https://cdn.svgporn.com/logos/vue.svg?response-content-disposition=attachment%3Bfilename%3Dvue.svg",
        })
    }
</script>