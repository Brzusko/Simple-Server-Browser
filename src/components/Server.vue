<template>
  <v-container>
    <v-card
        class="mx-auto"
        max-width="400"
    >
        <v-img
        class="white--text align-end"
        height="200px"
        :src="img"
        >
        <v-card-title>{{serverName}}</v-card-title>
        </v-img>

        <v-card-subtitle class="pb-0"><b>Server Addres: {{IP}}:{{PORT}}</b></v-card-subtitle>

        <v-card-text class="text--primary">
        <div>Current map: {{currentMap}}</div>

        <div>Slots {{playerCount}}/{{maxPlayers}}</div>
        </v-card-text>

        <v-card-actions>
        <v-btn
            color="orange"
            text
        >
            Details
        </v-btn>
        </v-card-actions>
    </v-card>
  </v-container>
</template>

<script>
  export default {
    name: 'ServerList',
    props: ["IP", "PORT", "currentMap", "maxPlayers", "playerCount", "serverName", "img"],
    data: () => ({

    }),
  }
</script>
