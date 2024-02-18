<template>
    <div>
        <h1>Directivas</h1>

        <h2>v-text</h2>
        <span>
            {{ titulo }} interpolando mi variable (v-text)
        </span>
        <hr>
        <br>

        <div v-html="html"></div>
        <hr>
        <br>

        <div>
            <h2>Directiva v-show</h2>
            <h3>Tu edad es de {{ edad }}</h3>
            <h3 v-show="edad >= 18">Mayor de edad</h3>
            <h3 v-show="edad < 18">Menor de edad</h3>
            <button @click="add()">Add</button>
        </div>
        <hr>
        <br>

        <div>
            <h2>Directiva v-if</h2>
            <h3>Tu edad es de {{ edad }}</h3>
            <h3 v-if="edad >= 18 && edad > 0 && edad < 100">Mayor de edad</h3>
            <h3 v-else-if="edad < 18 && edad > 0 && edad < 100">Menor de edad</h3>
            <h3 v-else>Edad Invalida</h3>
            <button @click="add()">Add</button>
            <button @click="dis()">Dis</button>
        </div>
        <hr>
        <br>

        <div>
            <h2>Directiva v-for</h2>
            <ul>
                <li v-for="usuario, index in usuarios" :key="index">{{ usuario }}-{{ index }}</li>
            </ul>
        </div>
        <hr>
        <br>

        <div @click="click()" class="contador">
            <h2>v-on</h2>
            Clicks: {{ clicks }}
        </div>
        <hr>
        <br>

        <div @click="click()">
            <h2>v-bind</h2>
            <img :src="url" alt="">
        </div>

    </div>
</template>

<script>

export default {
    data: () => ({
        titulo: "Hola desde Vue 3",
        html: "<h3> Soy un h3 - directiva v-html</h3>",
        edad: 16,
        usuarios: [
            "Melisa",
            "Fernando",
            "Raul",
            "José",
        ],
        clicks: 0,
        url: "https://cdn.svgporn.com/logos/vue.svg?response-content-disposition=attachment%3Bfilename%3Dvue.svg"
    }),
    methods: {
        add() {
            this.edad++
        },
        dis() {
            this.edad--
        },
        click() {
            this.clicks++
        }
    }
}

</script>

<style scoped>
div {
    text-align: center;
    margin: 0px 2rem;
}

.contador {
    background: tomato;
    color: snow;
    font-weight: bold;
    height: 200px;
}
</style>