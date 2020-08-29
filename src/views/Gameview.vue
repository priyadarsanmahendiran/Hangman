<template>
    <div class="gameview">
        <b-container class="text-center">
            <game-vue></game-vue>
        </b-container>
    </div>
</template>

<script>
import GameVue from '../components/Game.vue'

export default {
    name: 'Game',
    components: {
        GameVue
    },
    data() {
        return {
        }
    },
    created() {
    },
}
</script>