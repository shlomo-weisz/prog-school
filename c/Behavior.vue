<template>
    <p>test {{ behaviors }}</p>

    <div @click="clicked" class="div" :class="{ activ: isActiv}">
        {{ behaviors.name }}
    </div>
</template>

<script>
export default {
    emits: ['clicke'],
    props: { behaviors: Object },
    name: 'Behavior',

    data() {
        return {
            isActiv: false,
            scores: 0,

        }
    },
    methods: {
        clicked() {
            this.isActiv = !this.isActiv;
            this.$emit('clicke', this.scores);

        }
    },
    watch: {
        isActiv() {
            this.scores = this.isActiv ? (-1) * this.behaviors.score : this.behaviors.score;
        }
    },
    mounted() {
        ;
    },



}
</script>

<style>
.div {
    width: 100%;
    height: 50px;
    color: white;
    background-color: rgb(43, 172, 231);
    margin-bottom: 10px;
    cursor: pointer;
    border: 5px solid rgb(19, 20, 20);
    border-radius: 10px;
}

.activ {
    background-color: rgb(4, 52, 155);
}

.bad {
    background-color: rgb(255, 0, 0);
}
</style>