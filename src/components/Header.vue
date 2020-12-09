<template>
<header class="App-header">
    <section class="App-section">
        <div class="App-container App-container--xl">
            <div class="header__section">
                <div class="header__section--left">
                    <img src="../assets/logo-uz.svg" alt="logo uz-gent" class="header__section--img">
                    <img src="../assets/logo-u-gent.svg" alt="logo uz-gent" class="header__section--img">
                </div>
                <div class="header__section--mid">
                    <h1>Antibioticagids</h1>
                    <ul>
                        <li id="kinderen" v-bind:class="[selectedDoelgroep === 'kinderen' ? 'App-is-selected' :'']">
                            <div class="clickable" v-on:click="setDoelgroep('kinderen')">Kinderen</div>
                        </li>
                        <li id="volwassenen" v-bind:class="[selectedDoelgroep === 'volwassenen' ? 'App-is-selected' : '']">
                            <div class="clickable" v-on:click="setDoelgroep('volwassenen')">Volwassenen</div>
                        </li>
                    </ul>
                </div>
                <div class="header__section--right">
                    <ul>

                        <li><a href="https://www.bvikm.org/documenten" target="_blank" rel="noreferrer">IGGI</a></li>
                        <li><a href="https://www.uzgent.be/nl/zorgaanbod/mdspecialismen/OPAT/Paginas/default.aspx" target="_blank" rel="noreferrer">OPAT</a></li>

                    </ul>
                </div>
            </div>
        </div>
    </section>
</header>
</template>

<script>
//import logo_uz from '../assets/logo-uz.svg';
//import logo_u_gent from '../assets/logo-u-gent.svg';
export default {
    name: 'Header',
    props: {},
    data: () => {
        return {
            selectedDoelgroep: "",
        }
    },
    methods: {
        setDoelgroep: function (doelgroep) {
            this.selectedDoelgroep = doelgroep;
            this.$emit('setDoelgroep', doelgroep);
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style lang="scss" scoped>
@import '../scss/Variables.scss';

.header__section {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    @media screen and (min-width: $breakpoint-sm) {
        flex-direction: row;
        justify-content: space-between;
    }

    &--img {
        height: 1.6rem;
        margin-right: 1.4rem;

        @media screen and (min-width: $breakpoint-md) {
            height: 3.2rem;
        }
    }

    &--left {
        @media screen and (min-width: $breakpoint-sm) {
            flex-basis: 30%;
            text-align: left;
        }
    }

    &--mid {
        h1 {
            margin: 1rem 0;
        }

        ul {
            text-transform: uppercase;
            font-size: 1rem;
            font-weight: $font-weight-semibold;
            color: $color-primary;
            margin: 0 2rem;

            display: flex;
            flex-direction: row;
            justify-content: space-between;
        }

        @media screen and (min-width: $breakpoint-sm) {
            flex-basis: 40%;
            text-align: center;

            ul {
                display: flex;
                justify-content: center;

                li:first-child {
                    margin-right: 2rem;
                }
            }
        }
    }

    &--right {
        display: none;

        @media screen and (min-width: $breakpoint-sm) {
            display: flex;
            flex-basis: 30%;
            justify-content: flex-end;

            ul {
                display: flex;
                flex-direction: row;
                justify-content: flex-end;

                li:first-child {
                    margin-right: .6rem;
                }
            }
        }
    }
}
</style>
