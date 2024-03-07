<template>
    <div class="container mt-3">
        <MyHeader />
        <MyForm />
    </div>
</template>

<script>
import MyHeader   from "./components/MyHeader.vue";
import MyForm from "./components/MyForm.vue";

export default {
    components: {
        MyHeader,
        MyForm,
    }
}

</script>

<style scoped>

</style>