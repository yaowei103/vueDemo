<template>
    <div class="main">
        <my-component father-component="main"></my-component>
    </div>
</template>
<script>
import my-component from '../../components/index'
export default {
    name:'main',
    components:{
        my-component
    },
    
}
</script>