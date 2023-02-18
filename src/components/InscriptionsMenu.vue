<template>
    <div class="inscriptionMenu">
        <InscriptionInMenu :inscriptionScores="inscriptionScores(inscription.name)" v-for="(inscription, index) in inscriptions" :inscription="inscription" :key="index"/>
    </div>
</template>
<script>
import inscriptions from '../assets/items/inscriptions.json'
import InscriptionInMenu from './InscriptionInMenu.vue';

export default {
    data() {
        return {
            inscriptions: inscriptions.inscriptions
        }
    },
    props: {
        slots: {
            type: Object
        }
    },
    components: {
        InscriptionInMenu
    },
    methods: {
        inscriptionScores(inscriptionName) {
            let scores = 0;
            for(const key in this.slots) {
                this.slots[key][0] == inscriptionName ? scores++ : null;
                this.slots[key][1] == inscriptionName ? scores++ : null;
            }
            return scores
        }
    }
}
</script>
<style>
    .inscriptionMenu {
        margin: 50px auto;
        width: 40%;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
    }
</style>