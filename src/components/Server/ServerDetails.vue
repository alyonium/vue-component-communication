<template>
    <div class="col-xs-12 col-sm-6">
        <p v-if="currentServer === null">Server Details are currently not updated</p>
        <div v-else>Server {{ currentServer['id']}} with status {{ currentServer['status'] }}
            <button @click="changeStatus">Change status</button>
        </div>
    </div>
</template>

<script>
    import {eventBus} from "../../main";

    export default {
        data: () => ({
                currentServer: null,
        }),
        created() {
            eventBus.$on('setServer', (newServer) => {
                this.currentServer = newServer;
            })
        },
        methods: {
            changeStatus() {
                this.currentServer.status = 'Normal';
            }
        }
    }
</script>

<style>

</style>
