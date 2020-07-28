<template>
    <div>
        <b-button @click="move()">go</b-button>
        <b-button @click="home()">home</b-button>
        <b-form-input v-model="position" placeholder="Position eingeben" />
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
                this.$store.state.ownID = this.$socket.id
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

        },
        data: function () {
            return {
                connected: false,
            }
        },

    }
</script>

<style>

</style>