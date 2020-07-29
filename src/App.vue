<template>
    <div id="app">
        <Header />
        <b-container class="bv-example-row">
            <b-row>
                <b-col sm="6" offset="3">
                    <QuestionBox />
                </b-col>
            </b-row>
        </b-container>
    </div>
</template>

<script>
    import axios from 'axios'
    import Header from './components/Header.vue'
    import QuestionBox from './components/QuestionBox.vue'

    export default {
        name: 'App',
        components: {
            Header,
            QuestionBox
        },
        data() {
            return {
                questions: []
            }
        },
        async mounted() {
            const response = await axios.get('https://opentdb.com/api.php?amount=10')
            const quizData = response.data.results;
            console.log(quizData)
        }
    }
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
