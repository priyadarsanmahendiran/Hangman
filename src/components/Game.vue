<template>
    <div class="game">
        <b-container class="text-center">
            <div v-if="!lost_msg && !won_msg">
                <b-row v-if="!lost_msg">
                    <b-col>The Word: {{ stars }}</b-col>
                </b-row>
                <b-row>
                    <b-col>
                        <p>Guesses remaining {{ word_count }}</p>
                    </b-col>
                </b-row>
                <b-row style="padding-top: 20px">
                    <b-col>
                        <b-form inline class="guessform" @submit="guess" @reset="giveup">
                            <b-form-group>
                                <label for="guess">Guess the word</label>
                                <b-input id="guess" v-model="form.guess" type="text" required class="mb-2 mr-sm-2 mb-sm-0" placeholder="Letter"></b-input>
                                <b-button type="submit" variant="primary"> Guess </b-button>
                                <b-button type="reset" variant="danger"> Give Up </b-button>
                            </b-form-group>
                        </b-form>
                    </b-col>
                </b-row>
            </div>
            <b-row v-if="lost_msg">
                <b-col>
                    <p>You've lost the game! You killed you man!</p>
                    <p>The correct answer is {{lost_msg}}</p>
                </b-col>
            </b-row>
            <b-row v-if="won_msg">
                <b-col>
                   <p>You saved your man! {{won_msg}}</p> 
                   <p>The Answer is {{cname}}</p>
                </b-col>
            </b-row>
        </b-container>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Game',
    props : {
        
    },
    data() {
        return {
            form: {
                guess: ''
            },
            countryname: [],
            cname: '',
            stars: '',
            word_count: 0,
            lost_msg: '',
            won_msg: ''
        }
    },
    created() {
        axios.get('https://restcountries.eu/rest/v2/all')
        .then((response) => {
            response.data.forEach(element => {
                this.countryname.push(element.name);
            });
        })
        .then(() => {
            let cname = this.countryname[Math.floor(Math.random() * this.countryname.length)];
            let i = 0;
            for(i=0;i<cname.length;i++){
                this.stars += '*';
            }
            this.word_count = cname.length*2;
            this.cname = cname.toLowerCase();
        })
    },
    methods: {
        guess(){
            if(this.word_count == 1){
                this.lost_msg = this.cname;
            } else {
                let guessed_letter = this.form.guess;
                this.word_count -= 1;
                let n = this.cname.search(guessed_letter);
                if(n>=0){
                    alert('Correct guess');
                    let i=0;
                    let indices = [];
                    for(i=0;i<this.cname.length;i++){
                        if(this.cname[i] == guessed_letter){
                            indices.push(i);
                        }
                    }
                   for(i=0;i<indices.length;i++){
                       let ind = indices[i];
                       if(this.stars[ind] == ' '){
                           this.stars = this.replaceAt(this.stars,ind+1,guessed_letter);
                       } else {
                           this.stars = this.replaceAt(this.stars,ind,guessed_letter);
                       }
                   }
                } else {
                    alert('Incorrect Guess!');
                }
                this.form.guess='';
            }
            if(this.stars.indexOf('*') == -1){
                this.won_msg = 'You won';
            }
        },
        replaceAt(string, index, replacement) {
            return string.substr(0, index) + replacement + string.substr(index + replacement.length);
        },
        giveup(){
            this.lost_msg = this.cname;
        }
    },
}
</script>

<style scoped>
    .text-center{
        padding-top: 200px;
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        font-size: 20px;
    }
    .guessform{
        justify-content: center;
    }
</style>