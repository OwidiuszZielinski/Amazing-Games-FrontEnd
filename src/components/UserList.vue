<template fill-height>
    <v-container>
        <v-autocomplete v-model="userId" :items="users" @change="getId()" item-text="username" clearable 
            label="Users" required return-object>
        </v-autocomplete>
    </v-container>
</template>


<script>
import axios from 'axios'


export default {
    data() {
        return {
            userId: '',
            users: [],



        }
    },
    props: ['propuser'],

    model: { props: 'propuser', event: 'sendId' },



    created() {

        axios
            .get(this.$apiurl +'/users')
            .then(response => (this.users = response.data));
    },


    methods: {

        getId() {
            
            this.$emit('sendId', this.userId.id)

        }
    }
    
}
</script>
