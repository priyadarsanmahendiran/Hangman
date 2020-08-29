<template>
    <div class="entry">
        <b-container class="text-center">
            <b-row>
                <b-col>
                    <h1>Hangman!</h1>
                    <h5>Guess the name of the country if you can!</h5>
                </b-col>
            </b-row>
            <b-row class="button-proceed">
                <b-col class="text-center">
                    <router-link to="/game"><b-button>Proceed to play <b-icon-chevron-bar-right></b-icon-chevron-bar-right> </b-button></router-link>
                </b-col>
            </b-row>
        </b-container>        
    </div>
</template>

<script>
export default {
    name: 'Entry'
}
</script>

<style scoped>
    .entry{
        padding-top: 30px;
        padding-bottom: 10px;
    }

    .button-proceed{
        padding-top: 30px;
        background-color: transparent;
        color: white;
    }

</style>