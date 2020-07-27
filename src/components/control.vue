<template>
    <div>
        <b-button @click="move()">go</b-button>
        <b-button @click="home()">home</b-button>
        <b-form-input v-model="position" placeholder="Position eingeben"/>

    </div>
</template>

<script>
    export default {
        methods: {
            //CHANGEME: die Namen der Nachrichten die ihr mit emit() verschickt müssen mit dem Backend matchen
            move: function (preset) {
                console.log("Click button " + preset);
                this.$socket.emit('move', this.position);
            },
            home: function () {
                this.$socket.emit('home');
            }
        },
        sockets: {
            connect: function () {
                console.log('socket connected')
                this.connected = true;
                this.ownId = this.$socket.id
                this.$socket.emit("register_front")
            },
            disconnect: function () {
                console.log('socket disconnected')
                this.connected = false;
            },
            //CHANGEME: die Namen der Nachrichten hier reinkommen müssen mit dem Backend matchen (Funktionsname = Nachrichtenname)
            nsp_list: function (data) {
                console.log("NSPs:" + data);
            },
            update_queue: function (data) {
                this.currentQueue = data;
            },
            queue_ping: function () {
                this.$socket.emit("queue_pong")
            },
            update_timer: function (data) {
                this.currentTimer = data;
            },
            client_name: function (data) {
                this.clientName = data;
            }
        },
        data: function () {
            return {
                connected: false,
                currentQueue: [],
                ownId: "undefined",
                clientName: "undefined",
                currentTimer: 0,
                position: 0,
            }
        }

    }
</script>

<style>

</style>