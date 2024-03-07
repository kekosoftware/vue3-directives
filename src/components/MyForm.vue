<script>
import ProgressBar from './MyProgressBar.vue'
import TotalProyectos from './MyTotalProyects.vue'

export default {
    components: {
        ProgressBar,
        TotalProyectos,
    },
    data: () => ({
        proyecto: "",
        tipo: "",
        urgente: false,
        proyectos: [],
    }),
    methods: {
        registrarProyecto() {
            // Completado: false

            const proyecto = {
                proyecto: this.proyecto,
                tipo: this.tipo,
                urgente: this.urgente,
                completado: false,
            }
            this.proyectos.push(proyecto);
            
            this.proyecto = ""
            this.tipo = ""
            this.urgente = ""
        },
        cambiarEstado(proyecto, campo) {
            // this.proyectos[id].urgente = !this.proyectos[id].urgente 
            proyecto[campo] = !proyecto[campo]
        }
    },
    computed: {
        numeroProyectos() {
            return this.proyectos.length
        },
        porcentaje() {
            let completados = 0
            this.proyectos.map(proyecto => {
                if (proyecto.completado)
                    completados++
            })
            return (completados * 100 / this.numeroProyectos) || 0
        }
    }
}
</script>

<template>
    <div class="row">
        <div class="col-12 mb-3">
            <progress-bar :porcentaje="porcentaje"/>
        </div>
        <h3>Total proyectos: {{ numeroProyectos }}</h3>
        <div class="col12 col-md-4">
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
        <div class="col-12 col-md-8">
            <total-proyectos 
                :numeroProyectos="numeroProyectos"
                :proyectos="proyectos"
                :cambiarEstado="cambiarEstado"/>
        </div>
    </div>
</template>
