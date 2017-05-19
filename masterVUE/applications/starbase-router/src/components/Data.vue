<template>
    <div class="">
    Type: {{type}}    
    </div>
</template>
<script>
export default{
    data(){
        return {
            type: this.$route.params.type
        }
    },
    watch: {
        '$route': 'tweak'
    },
    methods: {
        tweak(){
            this.type = this.$route.params.type
        }
    }
}
    
</script>