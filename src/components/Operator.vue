<template>
    <div>
        <h1>Ingrese dos numeros y la operación</h1>
        <div class="row">
            <div class="col col-2">
                <div class="input-group input-group-sm">
                    <span class="input-group-text" id="inputGroup-sizing-sm">Nº1</span>
                    <input type="text" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-sm" v-model="numero1">
                </div>
            </div>
            <div class="col col-2">
                <div class="input-group input-group-sm">
                    <span class="input-group-text" id="inputGroup-sizing-sm">Op.</span>
                    <select class="form-select" aria-label="Default select example" v-model="operacion">
                        <option selected disabled>Seleccione...</option>
                        <option>+</option>
                        <option>-</option>
                        <option>*</option>
                        <option>/</option>
                    </select>                    
                </div>
            </div>
            <div class="col col-2">
                <div class="input-group input-group-sm">
                    <span class="input-group-text" id="inputGroup-sizing-sm">nº2</span>
                    <input type="text" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-sm" v-model='numero2'>
                </div>
            </div>
            <div class="col col-2">
                <button type="button" class="btn btn-primary btn-sm" @click="calcular">Calcular</button>
            </div>
        </div>
    </div>
</template>

<script>
import EventBus from '../bus'
export default {
    name:'Operator',
    data(){
        return{
            numero1: '',
            numero2: '',
            operacion:'Seleccione...',
        }
    },
    methods: {
        calcular: function(){
            EventBus.$emit('realizar', {numero1: this.numero1, numero2: this.numero2, operacion: this.operacion});
            this.numero1 = '';
            this.numero2 = '';
            this.operacion = 'Seleccione...';
        }
    }
}
</script>