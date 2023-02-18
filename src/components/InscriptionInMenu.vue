<template>
    <div class="inscription" @click="showInscriptionDesc">
        <img :src="inscription.image"/>
        <span>{{ this.inscriptionScores }}</span>
        <div class="inscriptionDescription" :class="{showInscriptionDesc: isShowInscriptionDesc}">
            <span>{{ inscription.name }}</span>
            <ul>
                <template v-for="(effect, index) in inscription.effects" :key="index">
                    <li v-if="effect != ''">{{ effect }}</li>
                </template>
            </ul>
        </div>
    </div>
</template>
<script>
export default {
    props: ['inscription', 'inscriptionScores'],
    data() {
        return {
            isShowInscriptionDesc: false
        }
    },
    methods: {
        showInscriptionDesc() {
            if(this.isShowInscriptionDesc) {
                this.isShowInscriptionDesc = false;
            } else {
                this.isShowInscriptionDesc = true;
            }
        },
    }
    
}
</script>
<style>
    .inscription {
        text-align: center;
        margin: 10px 0 10px 10px;
        padding-bottom: 40px;
        background-color: black;
        font-size: 30px;
        color: white;
        position: relative;
    }

    .inscription, .inscription img {
        width: 100px;
        height: 100px;
    }

    .inscriptionDescription {
        display: none;
    }

    .showInscriptionDesc {
        display: block;
        font-size: 15px;
        position: absolute;
        width: 400px;
        left: 50%;
        margin-left: -200px;
        padding: 20px;
        background-color: black;
    }

    .inscription:has(> .showInscriptionDesc) {
        z-index: 10;
    }

    
</style>