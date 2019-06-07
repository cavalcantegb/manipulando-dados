<template>
    <div>
        <h3>Buscando rivais</h3>
        <label>Time:</label>
        <input type="text" v-model="busca">
        <p>Rival: {{rival(busca)}}</p>

        <h3>Perfil</h3>
        <p>Time: {{nome}}</p>
        <p>Estadio: {{estadio}}</p>
    </div>
</template>

<script>
export default {
    name: 'LVTime',
    data() {
        return {
            nome: 'Cruzeiro',
            estadio: 'Mineirao',
            busca: '',
        }
    },
    methods: {
        rival(time) {
            switch( time.toLowerCase() ){
                case 'corithians':
                    return 'palmeiras'
                case 'santos':
                    return 'sao paulo'
                case 'flamengo':
                    return 'vasco'
                case 'cruzeiro':
                    return 'em minas eh marmelada'
                default: 
                    return 'nao encontrado' 
            }
        }
    }
}
</script>

<style>

</style>

