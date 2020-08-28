<template>
<div>
    <img :src="Logo" width="500" height="180" class="img-fluid mx-auto">
    <br />
    <br />
    <br />
    <button v-on:click="randomHero" class="btn btn-success mb-4">Start</button>
    <button v-on:click="attack" class="btn btn-danger mb-4">Attack</button>
    <button v-on:click="special" class="btn btn-warning mb-4">SpecialAttack</button>
    <button class="btn btn-info mb-4" @click.prevent="playSound('https://cdn.discordapp.com/attachments/746260527235334237/748885695959007383/One_Piece_Opening_1_HD_720p_Special_Edition_We_Are.mp3')"><span class="fa fa-play-circle-o"></span>Music</button>
    <div class="contianer">
        <div class="row">
            <div class="col-4">
                Name : {{NameHero}}
                <br />
                <img :src="ImgHero" :height="HPHero" class="mx-auto" />
                <br>
                HP : {{HPHero}}
                <br>
                <img v-bind:style="{width : HPHero + 'px'}" :src="BloodHero" alt height="25px" class=" mx-auto" />
            </div>
            <div class="col-4">
                <img :src="ImgF" width="500" height="200" class="img-fluid mx-auto">
                <img :src="ImgWin" class="img-fluid mx-auto" width="500" height="200" />
                <img :src="ImgDraw" class="img-fluid mx-auto" width="500" height="200" />
                <img :src="ImgLose" class="img-fluid mx-auto" width="500" height="200" />
            </div>
            <div class="col-4">
                Name : {{NameMonster}}
                <br />
                <img :src="ImgMonster" :height="HPMonster" class="mx-auto" />
                <br>
                HP : {{HPMonster}}
                <br>
                <img v-bind:style="{width : HPMonster + 'px'}" :src="BloodMonster" alt height="25px" class=" mx-auto" />
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    data: function () {
        return {
            BloodHero: "https://cdn.discordapp.com/attachments/746260527235334237/748860632693997595/BloodHero.png",
            BloodMonster: "https://cdn.discordapp.com/attachments/746260527235334237/748860627560300544/BloodMonster.png",
            Hero: "",
            Monster: "",
            NameHero: "",
            NameMonster: "",
            HPHero: "",
            HPMonster: "",
            SPATKHero: "",
            SPATKMonster: "",
            ATKHero: "",
            ATKMonster: "",
            ImgWin: "",
            ImgLose: "",
            ImgDraw: "",
            Logo: "https://cdn.discordapp.com/attachments/746260527235334237/748855839103778856/pngguru.com.png",
            Win: "https://cdn.discordapp.com/attachments/746260527235334237/748568823937892433/WIN0.png",
            Lose: "https://cdn.discordapp.com/attachments/746260527235334237/748568813561315328/LOSE0.png",
            Draw: "https://cdn.discordapp.com/attachments/746260527235334237/748568804375920640/DRAW0.png",
            ImgF: 'https://cdn.discordapp.com/attachments/746260527235334237/748568792455708872/FIGHT0.png',
            player: [{
                name: 'Luffy',
                hp: 800,
                image: 'https://cdn.discordapp.com/attachments/746260527235334237/747110861860110366/Luffy.png'
            }, {
                name: 'Zoro',
                hp: 700,
                image: 'https://cdn.discordapp.com/attachments/746260527235334237/747110863885828206/Zoro.png'
            }, {
                name: 'Ace',
                hp: 850,
                image: 'https://cdn.discordapp.com/attachments/746260527235334237/747110865593040896/Ace.png'
            }, {
                name: 'Kuzan',
                hp: 875,
                image: 'https://cdn.discordapp.com/attachments/746260527235334237/747110857129066556/Kuzan.png'
            }, {
                name: 'Law',
                hp: 800,
                image: 'https://cdn.discordapp.com/attachments/746260527235334237/747110859548917800/Law.png'
            }, {
                name: 'Jinba',
                hp: 850,
                image: 'https://cdn.discordapp.com/attachments/746260527235334237/747110858274111528/Jinba.png'
            }],
            monster: [{
                name: 'Doflamingo',
                hp: 850,
                image: 'https://cdn.discordapp.com/attachments/746260527235334237/747111044089905263/Doflamingo.png'
            }, {
                name: 'Crocodile',
                hp: 800,
                image: 'https://cdn.discordapp.com/attachments/746260527235334237/747110895511011338/Crocodile.png'
            }, {
                name: 'Lucci',
                hp: 800,
                image: 'https://cdn.discordapp.com/attachments/746260527235334237/747110860476121139/Lucci.png'
            }, {
                name: 'Garp',
                hp: 850,
                image: 'https://cdn.discordapp.com/attachments/746260527235334237/747110903891230800/Garp.png'
            }, {
                name: 'GekkoMoriah',
                hp: 700,
                image: 'https://cdn.discordapp.com/attachments/746260527235334237/747110855178584134/Gekko_moriah.png'
            }, {
                name: 'Akainu',
                hp: 900,
                image: 'https://cdn.discordapp.com/attachments/746260527235334237/747111050201268224/Akainu.png'
            }]
        }
    },
    methods: {
        randomHero: function () {
            this.Hero = Math.max(Math.floor(Math.random() * this.player.length));
            this.Monster = Math.max(Math.floor(Math.random() * this.monster.length));
            this.HPHero = this.player[this.Hero].hp
            this.HPMonster = this.monster[this.Monster].hp
            this.NameHero = this.player[this.Hero].name
            this.NameMonster = this.monster[this.Monster].name
            this.ImgHero = this.player[this.Hero].image
            this.ImgMonster = this.monster[this.Monster].image
            this.ImgWin = "";
            this.ImgLose = "";
            this.ImgDraw = "";
        },

        attack: function () {
            this.ATKHero = Math.max(Math.floor(Math.random() * 50) + 1, 10);
            this.ATKMonster = Math.max(Math.floor(Math.random() * 50) + 1, 10);
            if (this.HPHero != 0 && this.HPMonster != 0) {
                this.HPHero -= this.ATKMonster;
            }
            if (this.HPMonster != 0 && this.HPHero != 0) {
                this.HPMonster -= this.ATKHero;
            }
            if (this.HPMonster <= 0 & this.HPHero <= 0) {
                this.HPMonster = 0;
                this.HPHero = 0;
                this.ImgDraw = this.Draw;
            } else if (this.HPMonster <= 0) {
                this.HPMonster = 0;
                this.ImgWin = this.Win;
            } else if (this.HPHero <= 0) {
                this.HPHero = 0;
                this.ImgLose = this.Lose;
            }
        },
        special: function () {
            this.SPATKHero = Math.max(Math.floor(Math.random() * 100) + 1, 50);
            this.SPATKMonster = Math.max(Math.floor(Math.random() * 100) + 1, 50);
            if (this.HPHero != 0 && this.HPMonster != 0) {
                this.HPMonster -= this.SPATKHero;
            }
            if (this.HPHero != 0 && this.HPMonster != 0) {
                this.HPHero -= this.SPATKMonster;
            }
            if (this.HPMonster <= 0 & this.HPHero <= 0) {
                this.HPMonster = 0;
                this.HPHero = 0;
                this.ImgDraw = this.Draw;
            } else if (this.HPMonster <= 0) {
                this.HPMonster = 0;
                this.ImgWin = this.Win;
            } else if (this.HPHero <= 0) {
                this.HPHero = 0;
                this.ImgLose = this.Lose;
            }
        },
        playSound(sound) {
            if (sound) {
                var audio = new Audio(sound);
                audio.play();
            }
        }
    }
}
</script>

<style>
body {
    font-family: 'Russo One', sans-serif;
}
</style>
