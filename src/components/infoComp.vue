<template lang="">
    <div>
        {{firstName}}
        {{lastName}}
        {{objectData}}

    </div>

    <slot></slot>
</template>
<script>
export default {
    props :['firstName','lastName','objectData']
    
    
}
</script>
<style lang="">
    
</style>