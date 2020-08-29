<template>
  <div>
    <button @click="randomStart()" class="btn btn-danger btn-lg mb-2">Start</button>
    <div class="row">
      <div class="col">
        <button @click="randomDamage(10,50)" class="btn btn-primary mb-4">Attack</button> 
        <button @click="randomDamageSP(80,100)" class="btn btn-info mb-4">SP Attack</button> 
      </div>
    </div>
    <div class="container-fluid">
      <div class="row">
        <div class="col">
          <div class="alert alert-primary" role="alert">Hero : {{randomPlayer}} HP : {{hp1}}</div> 
          <img :src="image1" class="img-fluid" />
        </div>
        <div class="col">
          <div class="alert alert-primary" role="alert">Hero : {{randomMonster}} HP : {{hp2}}</div> 
          <img :src="image2" class="img-fluid" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      randomAttack: "",
      randomSpAttack: "",
      image1: "",
      image2: "",
      hp1: "",
      hp2: "",
      win: "https://obs.line-scdn.net/0hdIGxrUs0O2Z6ARNxWLBEMUBXOAlJbShlHjdqZSZvZVIDN30zETNzU1ZUYlFXY3w4E2dxAV8JIFcEYS40QTJz",
      lose: "data:image/jpeg;base64,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", 
      player: [
        {
          name: "Captain America", 
          hp: 500, 
          image: "https://i.pinimg.com/564x/3a/4e/9d/3a4e9d0ecf3e916ae5835d03e49bd3f1.jpg",
        },
        {
          name: "Iron Man",
          hp: 450, 
          image: "https://รูปการ์ตูนน่ารักๆ.com/wp-content/uploads/2017/12/82b9fd5f7e5bc27dcdcc12347a68fe89.jpg", 
        },
        {
          name: "Thor", 
          hp: 400, 
          image: "https://i.pinimg.com/564x/5a/c3/7f/5ac37ff664d46de90c1756c8361df8f0.jpg", 
        },
        {
          name: "The Huge", 
          hp: 420,
          image: "https://i.pinimg.com/564x/91/e7/f1/91e7f1fc1f71931e730d7e6810ac07dd.jpg", 
        },
        {
          name: "The Flash", 
          hp: 300, 
          image: "https://i.pinimg.com/564x/da/49/3c/da493cf96d8e12385a0df274a74f89aa.jpg",
        },
        {
          name: "Deadpool",
          hp: 350, 
          image: "https://i.pinimg.com/564x/0d/18/0c/0d180cf154047d0e43b1b72656d68d3d.jpg", 
        },
      ],
      randomPlayer: "",
      monster: [
        {
          name: "Venom", 
          hp: 350, 
          image: "https://i.pinimg.com/564x/30/e4/c8/30e4c89fc5211efd34ef4df3cf8a4c22.jpg", 
        },
        {
          name: "Thanos", 
          hp: 480, 
          image: "https://i.pinimg.com/564x/2c/16/8a/2c168a24a066e44e3b0903f453449fe5.jpg", 
        },
        {
          name: "Joker",
          hp: 300, 
          image: "https://i.pinimg.com/564x/70/ed/5f/70ed5f86bb018e621bcdaa5ce125b0b9.jpg", 
        },
        {
          name: "Alien", 
          hp: 320, 
          image: "https://i.pinimg.com/564x/2b/c8/b2/2bc8b23c8754c84b619787feaeeeb606.jpg", 
        },
        {
          name: "Godzilla", 
          hp: 400, 
          image: "https://i.pinimg.com/564x/ab/ff/3c/abff3c0fa123bd7c749552b6238c4a62.jpg", 
        },
      ],
      randomMonster: "",
    };
  },

  props: {
    Label: String,
  },

  methods: {
    randomStart: function () {
      var chosenNumber1 = Math.floor(Math.random() * this.player.length);
      this.randomPlayer = this.player[chosenNumber1].name;
      this.hp1 = this.player[chosenNumber1].hp;
      this.image1 = this.player[chosenNumber1].image;

      var chosenNumber2 = Math.floor(Math.random() * this.monster.length);
      this.randomMonster = this.monster[chosenNumber2].name;
      this.hp2 = this.monster[chosenNumber2].hp;
      this.image2 = this.monster[chosenNumber2].image;
    },

    randomDamage: function (min, max) {
      this.randomAttack = Math.max(Math.floor(Math.random() * max) + 1, min);
      if (this.hp1 != 0 && this.hp2 != 0) {
        this.hp1 -= this.randomAttack;
      }
      if (this.hp1 != 0 && this.hp2 != 0) {
        this.hp2 -= this.randomAttack;
      }
      if (this.hp1 <= 0) {
        this.hp1 = 0;
        this.image1 = this.lose;
      }
      if (this.hp2 <= 0) {
        this.hp2 = 0;
        this.image2 = this.win;
      }
    },

    randomDamageSP: function (min, max) {
      this.randomAttack = Math.max(Math.floor(Math.random() * max) + 1, min);
      if (this.hp1 != 0 && this.hp2 != 0) {
        this.hp2 -= this.randomAttack;
      }
      if (this.hp1 <= 0) {
        this.hp1 = 0;
        this.image1 = this.lose;
      }
      if (this.hp2 <= 0) {
        this.hp2 = 0;
        this.image2 = this.win;
      }
    },
  },
};
</script>

<style>
</style>