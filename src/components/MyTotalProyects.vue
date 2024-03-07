<template>
    <div class="table-responsive table-hover">
        <table class="table">
            <thead>
                <tr>
                    <th>#</th>
                    <th>Proyecto</th>
                    <th>Tipo</th>
                    <th>Urgente</th>
                    <th>Completado</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(proyecto, index) in proyectos" :key="index">
                    <td>{{ index }}</td>
                    <td>{{ proyecto.proyecto }}</td>
                    <td>{{ proyecto.tipo }}</td>
                    <td @click="cambiarEstado(proyecto, 'urgente')" :class="proyecto.urgente ? 'bg-success' : 'bg-danger'">{{ proyecto.urgente ? "SI" : "NO" }}</td>
                    <td @click="cambiarEstado(proyecto, 'completado')" :class="proyecto.completado ? 'bg-success' : 'bg-danger'">{{ proyecto.completado ? "COMPLETE" : "INCOMPLETE" }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    props: [
        'numberoProyectos',
        'proyectos',
        'cambiarEstado',
    ]
}
</script>

<style>

</style>