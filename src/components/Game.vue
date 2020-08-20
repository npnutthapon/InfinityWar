<template>
    <div>
        <p>HP Player {{randomDamageNo(0,4)}} {{player[randomDamageNo(0,4)-1].name}}</p>
        <p>HP Monster {{randomDamageNo(0,4)}} {{monster[randomDamageNo(0,4)-1].name}}</p>
        <hr>
        name={{aPlayer.name}}
        hp={{aPlayer.hp}}

        name={{aMonster.name}}
        hp={{aMonster.hp}}
        <hr>
       <button @click="start">Start</button>
       <button>Attack</button>
       <button>Spacial Attack</button>
    </div>
</template>
<script>
export default {
    data:function(){
        return{
            aPlayer:{name:'',hp:''},
            aMonster:{name:'',hp:''},
            player :[{name:'Luffy',hp:100},{name:'Zoro',hp:90},{name:'Sanji',hp:80},{name:'Usopp',hp:50},{name:'Nami',hp:40}],
            monster:[{name:'Doflamingo',hp:100},{name:'Crocodile',hp:90},{name:'lucci',hp:80}]
        }
    },
    methods:{
        randomDamageNo: function(min, max) {             
            return Math.max(Math.floor(Math.random() * max) + 1, min);    
            },
        start: function(){
            //random player
            this.aPlayer = this.player[this.randomDamageNo(1,3)-1]
            //random monster
            this.aMonster = this.monster[this.randomDamageNo(1,3)-1]
            },
        attack : function(){
            
            }
    }
}
</script>
<style lang="">
    
</style>