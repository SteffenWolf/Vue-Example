<template>
  <div id="app">
    <header>
      <button @click='toggle'>Create</button>
      <h1>Battle Bots</h1>
      <button @click='battleBot'>Collection</button>
      <hr>
    </header>
    
    <section v-if='showCreate'>
      <form action="">
        <input type="text" placeholder="Bot Name" v-model='botName'>
          <br>
        <input type="number" min="0" step='1' placeholder="Attack Value" v-model='attackVal'>
          <br>
        <input type="number" min="0" step='1' placeholder="Health Value" v-model="healthVal">
          <br>
        <button @click='addBot'>Submit</button>
        <button type='reset'>Clear</button>

      </form>
    </section>

    <section v-else>
      <h3>{{bot1}}</h3>
      <h3>{{bot2}}</h3>
      <hr>
      {{botObj}}
      <Bot v-for='(botObj, i) in allBots' :key='i' :botObj= 'botObj'/>


    </section>


  </div>
</template>

<script>
import Bot from './components/Bot'

export default {
  name: 'app',

  data: function(){
    return{
      showCreate: true,
      botName: '',
      attackVal: '',
      healthVal: '',
      allBots: [],
      bot1: 'Contestant #1: Select a bot from below',
      bot2: 'Contestant #2: Select a bot from below',
      battleZone: [A, B]

    }
  },

  methods: {
    toggle: function() {
      this.showCreate = !this.showCreate
    },

    addBot() {
      const newBot = {botName: this.botName, attackVal: this.attackVal, healthVal: this.healthVal};
      this.allBots.push(newBot);
      this.botName = '';
      this.attackVal = '';
      this.healthVal = '';
      this.toggle();
    },

    battleBot() {
      var winner = this.battleZone[Math.floor(Math.random()*this.battleZone.length)]
      return winner
      console.log(winner)

    }
  },

  components: {
    Bot: Bot

  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
