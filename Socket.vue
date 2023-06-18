<template>
    <div>
        <market-channel></market-channel>
        <private-channel></private-channel>
    </div>
</template>

<script>
import Echo from 'laravel-echo';
import {mapGetters} from 'vuex'

// Public channels
import MarketChannel from "@/Store/Channels/Public/Market/MarketChannel";

// Private channel
import PrivateChannel from "@/Store/Channels/Private/PrivateChannel";

export default {
    components: {PrivateChannel, MarketChannel},
    computed: mapGetters({
        socket: 'getSocket',
        user: 'getUser',
    }),
    methods: {
        loadSocket: function () {
            // If there is already connected echo server shut it down
            if (window.Echo) window.Echo.disconnect();

            window.io = require('socket.io-client');

            window.Echo = new Echo({
                broadcaster: 'socket.io',
                host: window.location.hostname,
                auth: { headers: {
                    'Accept': 'application/json',
                    'Content-Type': 'application/json',
                    'Origin': route('home'),
                }}
            });

            // On socket connect dispatch socket and store socket id
            window.Echo.connector.socket.on('connect', () => {
                this.$store.dispatch('setSocket', {
                    socket: window.Echo.socketId()
                });
            });

            // On socket disconnect dispatch socket with empty value
            window.Echo.connector.socket.on('disconnect', () => {
                this.$store.dispatch('setSocket', {
                    socket: null
                });
            });
        }
    },
    data() {
        return {
            connectionTimeout: 2000,
        }
    },
    mounted() {
        // Initial load
        if(!this.socket) {
            this.loadSocket();
        }

        // Cycling socket loading to reconnect
        setTimeout(() => { if(!this.socket) this.loadSocket(); }, this.connectionTimeout);
    },

    watch: {
        user: function () {
            this.loadSocket();
        }
    },
}
</script>
