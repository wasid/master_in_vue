<template>
    <div class="col-md-12">
        <Item
            v-for="(item, index) in items"
            key= "index"
            :passed-item="item"
            :type="type"
        />
        
    </div>
</template>
<script>
import Item from "./Item.vue"
export default{
    data(){
        return {
            type: this.$route.params.type,
            items: []
        };
    },
    watch: {
        '$route': 'tweak'
    },
    methods: {
        tweak(){
            this.items = [];
            this.type = this.$route.params.type;
            let initial_ids = [1,3,4,5,6,7];
            
            for (let i in initial_ids) {
                let id = initial_ids[i];
                fetch(`http://swapi.co/api/${this.type}/${id}`, {
                method:"GET"
              })
              .then(respose => respose.json())
              .then(json => this.items.push(json));
            }
        }
    },
        
    created(){
        this.tweak();
    },
    components:{
        Item
    }
};
    
</script>