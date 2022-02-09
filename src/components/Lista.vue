<template>
    <div>
        <ul class="list-group">
            <li v-for="(item, index) of ordLista" :key="item.id" @click="aumentar(index)"
            class="list-group-item d-flex justify-content-between align-items-center">
                {{item.nombre}}
                <span class="badge bg-primary rounded-pill">{{item.cantidad}}</span>
            </li>
        </ul>
        <div class="d-grid gap-2">
            <button class="btn btn-primary" type="button" @click="reset">Resetear</button>
        </div>
    </div>
</template>

<script>
    
import {mapState, mapMutations} from 'vuex';

export default {
    name: 'Lista',
    computed:{
        ...mapState(['frutas']),
        ordLista(state){
            
            return state.frutas.sort((a, b) => b.cantidad - a.cantidad);
        }
    },
    methods:{
        ...mapMutations(['aumentar', 'reset'])
    }
}
</script>