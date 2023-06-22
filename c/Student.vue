<template>
    <div>

        <table>
            <tr>{{ idStudent }}</tr>
            <tr>{{ nameStudent }}</tr>
            <tr v-for="behavior in behaviors" :key="behavior.id" :alt="behavior.description"
            @clicke="addScore" :class="{bad: (behavior.type == 'bad')}">
                <Behavior 
                 :behaviors="behavior" />
            
            </tr>
            <tr>{{ scores }}</tr>
        </table>        
    </div>
   
</template>

<script>
import datas from './list.json';
import Behavior from './Behavior.vue';
export default {
    name: 'Student',
    props: {
        nameStudent: String,
        idStudent: Number,
    },
    components: {
        Behavior,
        
        
    },
    data() {
        return {
            behaviors: datas,
            scores: 0,

            
        }
    },
    mounted() {
        fetch('./list.json')
            .then((response) => response.json())
            .then((data) => {
                this.behaviors = data;
            });
    },
    methods: {
        addScore(score) {
            this.scores = this.scores + score;
        }
        
    }
}
</script>

<style scoped>
table {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    background-color: blanchedalmond;
}
li {
    display: inline-block;
    list-style-type: none;
}
.bad {
    background-color: rgb(255, 0, 0);
}

</style>