<template>
    <div>
        <h1 v-bind:style="{ display: mostrar}">
            Resultado: {{numero1}} {{operacion}} {{numero2}} = {{resultado}}
        </h1>
        <div class="col mx-5" v-bind:style="{ display: mostrar}">
            <p>{</p>
            <p class="mx-4">"a": {{numero1}}</p>
            <p class="mx-4">"b": {{numero2}}</p>
            <p class="mx-4">"c": {{resultado}}</p>
            <p class="mx-4">operador: "{{operacion}}"</p>
            <p>}</p>
        </div>
    </div>
</template>

<script>
import EventBus from '../bus'
export default {
    name:'Resultado',
    data(){
        return{
            numero1: '',
            numero2: '',
            operacion: '',
            resultado: '',
            mostrar: 'none',
            objeto: '',
        }
    },
    created: function(){
        EventBus.$on('realizar', (object) =>{
            this.numero1 = object.numero1;
            this.numero2 = object.numero2;
            this.operacion = object.operacion;
            this.realizarOp(this.operacion)
            this.mostrar = '';
            this.objeto = object
        })
    },
    methods: {
        realizarOp: function(operacion){
            if (operacion == '+') {
                this.resultado = this.numero1 + this.numero2
            }else if (operacion == '-') {
                this.resultado = this.numero1 - this.numero2
            }else if (operacion == '*') {
                this.resultado = this.numero1 * this.numero2
            }else if (operacion == '/') {
                this.resultado = this.numero1 / this.numero2
            }
        }
    }

}
</script>

<style scoped>
.col{
    background-color: rgb(214, 214, 214);
    border: 1px solid rgb(109, 108, 108);
}
p{
    margin-top: 0;
    margin-bottom: 0;
}
</style>