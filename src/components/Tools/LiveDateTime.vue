<template>
    <div class="taxt-subtitle-1 ml-4">
        {{data}}
    </div>
</template>
<script>
import { format } from 'date-fns';
export default {
    data(){
        return {
            data: ''
        }
    },
    mounted(){
        this.getDate()
    },
    methods:{
        getDate(){
            this.data = format(new Date(), 'MMMM d, H:mm:ss')
            setTimeout(this.getDate, 1000)
        }
    }
}
</script>