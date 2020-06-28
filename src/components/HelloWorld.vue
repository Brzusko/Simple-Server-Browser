<template>
  <v-container>
    <v-row class="">
      <v-col
        v-for="(server, i) in servers"
        :key="i"
        cols="12"
      >
      <server
        :serverName="server.serverName"
        :IP="server.IP"
        :PORT="server.PORT"
        :maxPlayers="server.maxPlayers"
        :playerCount="server.playerCount"
        :currentMap="server.currentMap"
        :img="GetRandomIMG()"
      />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  import Server from './Server'
  export default {
    name: 'ServerList',

    components :{
      Server
    },
    data: () => ({
      ADDRESS: "http://127.0.0.1:7171/",
      servers: [],
      imgs:[
        "https://i.imgur.com/3b8Mx2C.png",
        "https://i.imgur.com/2IlrmBP.png",
        "https://i.imgur.com/dMC3pTQ.png",
        "https://i.imgur.com/BDyTSUS.png",
        "https://i.imgur.com/9g1cJoF.png"
      ]
    }),
    methods: {
      async FetchServers() {
        this.servers = []
        let result = await this.$http(`${this.ADDRESS}getservers`);
        if(result.data != undefined)
          for(let i = 0; i < result.data.length; i++)
            this.servers.push(result.data[i]);
      },
      GetRandomIMG(){
        let index = Math.floor(Math.random() * this.imgs.length);
        return this.imgs[index];
      }
    },
    async mounted() {
      await this.FetchServers();
      setInterval(async() => {
        await this.FetchServers();
      }, 20000)
    }
  }
</script>
