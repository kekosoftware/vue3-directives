<script>
export default {
    data: () => ({
        proyecto: "",
        tipo: "",
        urgente: false,
        proyectos: [],
    }),
    methods: {
        registrarProyecto() {
            const proyecto = {
                proyecto: this.proyecto,
                tipo: this.tipo,
                urgente: this.urgente,
            }
            this.proyectos.push(proyecto);
            
            this.proyecto = ""
            this.tipo = ""
            this.urgente = ""
        },
        cambiarEstado(id) {
            this.proyectos[id].urgente = !this.proyectos[id].urgente 
        }
    },
    computed: {
        numeroProyectos() {
            return this.proyectos.length
        }
    }
}
</script>

<template>
    <div class="row">
        <form @submit.prevent="registrarProyecto()">
            <div class="mb-3">
                <label for="proyecto" class="form-label">Proyecto</label>
                <input v-model.trim="proyecto" type="text" class="form-control" id="proyecto" required>
            </div>
            <div class="mb-3">
                <label for="actividad" class="form-label">Actividad: </label>
                <select v-model.trim="tipo" class="form-select" aria-label="" required>
                    <option value="" disabled selected>Seleccione un tipo ...</option>
                    <option value="1">Aplicación con Vue.js</option>
                    <option value="2">Backend service con node.js</option>
                    <option value="3">App mobile con React Native</option>
                </select>
            </div>
            <div class="mb-3 form-check">
                <label class="form-check-label" for="urgente">Urgente</label>
                <input v-model="urgente" type="checkbox" class="form-check-input" id="urgente">
            </div>
            <button type="submit" class="btn btn-primary">Guardar</button>
        </form>
    </div>
    <hr>
    <h3>Total proyectos: {{ numeroProyectos }}</h3>

    <div class="table-responsive table-hover">
        <table class="table">
            <thead>
                <tr>
                    <th>#</th>
                    <th>Proyecto</th>
                    <th>Tipo</th>
                    <th>Urgente</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(proyecto, index) in proyectos" :key="index">
                    <td>{{ index }}</td>
                    <td>{{ proyecto.proyecto }}</td>
                    <td>{{ proyecto.tipo }}</td>
                    <td @click="cambiarEstado(index)" :class="proyecto.urgente ? 'bg-success' : 'bg-danger'">{{ proyecto.urgente ? "SI" : "NO" }}</td>
                </tr>
            </tbody>
        </table>
    </div>

    <div class="row"><br></div>
    <div class="row">
        <label for="">Proyecto: 
            <pre>{{ proyecto }}</pre>
        </label>
        <label for="">Tipo: 
            <pre>{{ tipo }}</pre>
        </label>
        <label for="">Urgente: 
            <pre>{{ urgente }}</pre>
        </label>
    </div>
</template>
