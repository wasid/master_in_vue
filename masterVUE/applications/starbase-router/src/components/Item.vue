<template>
   <div class="col-md-4" @click="switcher">
        <div class="character-card">
            <div class="card-block">
                <h4 class="catd-title">{{item.name}}</h4>
                <div v-for="(value, key, index) in item">
                    <div v-if="index < 5">
                        <strong>{{key}}</strong>: {{value}}
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>
<script>
export default{
   props: ['passedItem', 'type'],
   data(){
        return {
            item: {}
        };
    },
    methods: {
        switcher(){
            
            let rand_id = Math.floor(Math.random() * 63) + 1;
                fetch(`http://swapi.co/api/${this.type}/${rand_id}`, {
                method:"GET"
              })
              .then(respose => respose.json())
              .then(json => this.item = json);
        }
    },
        
    created(){
        this.item = this.passedItem;
    }
};
    
</script>