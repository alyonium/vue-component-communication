<template>
    <div class="col-xs-12 col-sm-6">
        <ul class="list-group">
            <v-server v-for="server in servers" :serverIndex="server.id" :onSetServer="setServer" :isActive="server.isActive"/>
        </ul>
    </div>
</template>

<script>
    import Server from './Server.vue'
    import { eventBus } from "../../main"

    export default {
        components: {
            'v-server': Server,
        },
        data: function() {
            return {
                servers: [
                    { id: 1, status: 'Normal', isActive: false},
                    { id: 2, status: 'Critical', isActive: false},
                    { id: 3, status: 'Unknown', isActive: false},
                    { id: 4, status: 'Too many requests', isActive: false},
                    { id: 5, status: 'Normal', isActive: false},
                ],
            }
        },
        methods: {
          setServer(id) {
              this.servers = this.servers.map(el => {
                  el.isActive = false;
                  return el;
              });
              this.servers.find(el => el.id === id).isActive = true;
              eventBus.$emit('setServer', this.servers.find(el => el.id === id));
          },
        }
    }
</script>

<style>

</style>
