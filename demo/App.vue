<template>
    <div id="app">
        <!--Example dependecies-->
        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bulma/0.4.1/css/bulma.min.css">
        <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
        <a :href="repoUrl"><img
                style="position: absolute; top: 0; right: 0; border: 0;"
                src="https://camo.githubusercontent.com/38ef81f8aca64bb9a64448d0d70f1308ef5341ab/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6769746875622f726962626f6e732f666f726b6d655f72696768745f6461726b626c75655f3132313632312e706e67"
                alt="Fork me on GitHub"
                data-canonical-src="https://s3.amazonaws.com/github/ribbons/forkme_right_darkblue_121621.png"></a>

        <!--Example Elements-->
        <section class="hero">
            <div class="hero-body" style="padding: 1rem 0">
                <div class="container">
                    <div class="columns">
                        <div class="column is-8 is-offset-3" style="display: flex; align-items: center;">
                            <div class="is-pulled-left">
                                <img width="350px" src="./assets/logo.png">
                            </div>
                            <div class="is-pulled-left" style="text-align: left">
                                <h1 class="title text-medium-grey" style="margin-bottom: .5rem">
                                    Floating Action Button
                                </h1>
                                <hr class="is-marginless">
                                <h2 class="subtitle text-light-grey" style="margin-top: .5rem">
                                    A Vue Component
                                </h2>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section class="section" style="padding-top: .5rem">
            <div class="container">
                <div class="columns">
                    <div class="column is-8 is-offset-2">
                        <div class="box formated">
                            <div class="heading">
                                <div class="columns">
                                    <div class="column">
                                        <i class="material-icons top-left">code</i>
                                        <span class="is-pulled-right"><b>Example</b></span>
                                    </div>
                                </div>
                            </div>
                            <div class="content">
                                <div class="columns">
                                    <div class="column">
                                        <div class="field is-pulled-left">
                                            <label class="label">Color</label>
                                            <p class="control">
                                                <chrome-picker v-model="colors"/>
                                            </p>
                                        </div>
                                    </div>
                                    <div class="column">
                                        <div class="field">
                                            <label class="label is-pulled-left">Position</label>
                                            <br/>
                                            <p class="control">
                                            <span class="select">
                                              <select v-model="position">
                                                <option v-for="pos in positions">{{pos}}</option>
                                              </select>
                                            </span>
                                            </p>
                                            <label class="label is-pulled-left">First Icon</label>
                                            <p class="control">
                                                <input type="text" class="input" v-model="firstIcon">
                                            </p>
                                            <label class="label is-pulled-left">Second Icon</label>
                                            <p class="control">
                                                <input type="text" class="input" v-model="secondIcon">
                                            </p>
                                            <p class="control">
                                                <label class="checkbox">
                                                    <input type="checkbox" v-model="simple"> Simple mode ?
                                                </label>
                                            </p>
                                            <label class="label is-pulled-left">Main Icon</label>
                                            <p class="control">
                                                <input type="text" class="input" v-model="mainIcon">
                                            </p>
                                        </div>
                                    </div>
                                </div>
                                <div class="columns">
                                    <div class="column has-text-centered">
                                        <a :href="repoUrl">Installation & Code usage</a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <footer class="footer">
            <div class="container">
                <div class="content has-text-centered">
                    <p>
                        <strong>Floating Action Button Vue Directive</strong> by <a
                            :href="teamUrl">Pygmy Team</a>.
                    </p>
                    <p>
                        <small>Used dependencies for this demo: <a href="http://bulma.io">bulma</a> | <a
                                href="https://github.com/xiaokaike/vue-color">vue-color</a></small>
                    </p>
                </div>
            </div>
        </footer>
        <fab
                :position="position"
                :simple="simple"
                :icon-name="mainIcon"
                :bg-color="colors.hex"
                :actions="[{name: 'alertMe',icon: firstIcon},{name: 'alertMe',icon: secondIcon}]"
                @alertMe="alert"
                @click="alertSimple"
        ></fab>
    </div>
</template>

<script>
    import FAB from '../src/FAB.vue';
    import {Chrome} from 'vue-color';

    const teamUrl = 'https://github.com/PygmySlowLoris';
    const repoUrl = 'https://github.com/PygmySlowLoris/vue-fab';

    const defaultProps = {
        hex: '#194d33',
        hsl: {
            h: 150,
            s: 0.5,
            l: 0.2,
            a: 1
        },
        hsv: {
            h: 150,
            s: 0.66,
            v: 0.30,
            a: 1
        },
        rgba: {
            r: 25,
            g: 77,
            b: 51,
            a: 1
        },
        a: 1
    };

    export default {
        name: 'app',
        components: {
            fab: FAB,
            'chrome-picker': Chrome
        },
        data(){
            return {
                repoUrl: repoUrl,
                teamUrl: teamUrl,
                positions: [
                    'bottom-right',
                    'bottom-left',
                    'top-right',
                    'top-left',
                ],
                position: 'bottom-right',
                colors: defaultProps,
                mainIcon: 'add',
                firstIcon: 'cached',
                secondIcon: 'add_alert',
                simple: false
            }
        },
        methods: {
            alert(){
                alert('You have clicked me :)');
            },
            alertSimple(){
                alert('You have clicked me and i am in simple mode :)');
            }
        }
    }
</script>

<style scoped>
    #app {
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
    }

    .pointer {
        cursor: pointer;
    }

    h1, h2 {
        font-weight: normal;
    }

    hr {
        background-color: transparent;
        border: none;
        display: block;
        height: inherit;
        margin: 1.5rem 0;
        border-top: dashed 1px;
    }


    li {
        display: inline-block;
        margin: 0 10px;
    }

    a {
        color: #0b99b9;
        text-decoration: underline;
    }

    .text-medium-grey {
        color: #333;
    }

    .text-light-grey {
        color: #888;
    }

    .box.formated {
        position: relative;
        padding: 0;
    }

    .box.formated .heading {
        font-size: 1rem;
        text-transform: capitalize;
        padding: .8rem 1.5rem;
        background-color: #fafafa;
    }

    .box.formated .content {
        padding: 1rem 2rem;
    }

    i.top-left {
        position: absolute;
        left: 1.5rem;
        top: 0.8rem;
    }

    .vertical-separator {
        display: flex; justify-content: space-around;
    }

    .vertical-separator .line {
        border-right: 1px solid #cccccc;
    }
</style>
