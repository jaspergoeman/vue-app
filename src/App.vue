<template>
<div>
    <Header @setDoelgroep="setDoelgroep" />
    <Beam  @setTopic="setTopic" @setSubgroup="setSubgroup" />
</div>
</template>

<script>
import Header from './components/Header.vue';
import Beam from './components/Beam.vue';

export default {
    name: 'App',
    data: () => {
        return {
            doelgroep: String,
            topic: String,
            subgroup: String
        }
    },
    components: {
        Header,
        Beam,
    },
    methods: {
        setDoelgroep(doelgroep) {
            this.doelgroep = doelgroep;
            console.log(this.doelgroep);
        },
        setSubgroup(subgroup) {
            this.subgroup = subgroup;
            console.log(this.subgroup);
        },
        setTopic(topic) {
            this.topic = topic;
            console.log(this.topic);
        }
    }
}
</script>

<style lang="scss">
@import './scss/Variables.scss';

// ------------------------------------------------------------------
// Typography
// ------------------------------------------------------------------
@font-face {
  font-family: 'Arboria-Book';
  src: local('Arboria'), url(./fonts/Arboria-Medium.otf) format('truetype');
}
body {
  font-family: 'Arboria', sans-serif;
  font-weight: 500;}
h1 {
    color: $color-primary;
    text-transform: uppercase;
    font-size: 2.2rem;
}

ul {
    margin-inline: 0;
    padding-inline: 0;
    margin-block: 0;
}

li {
    list-style-type: none;
}

a {
    text-decoration: none;
    color: $color-link;
    cursor: pointer;
}

// ------------------------------------------------------------------
// STANDARDS
// ------------------------------------------------------------------

.clickable {
    cursor: pointer;
}

.clickable:hover {
    color: $color-third;
}

body {
    margin: 0;
}

// ------------------------------------------------------------------
// APP container & section
// ------------------------------------------------------------------

.App {
    &-container {
        position: relative;
        margin: 0 auto;
        padding: 0 $padding-section/2;

        // ------------------------------------------------------------------
        // CONTAINER WIDTHS
        // -----------------------------------------------------------------

        &--sm {
            @media screen and(min-width: $breakpoint-sm) {
                max-width: $container-sm;
            }
        }

        &--md {
            @media screen and(min-width: $breakpoint-sm) {
                max-width: $container-sm;
            }

            @media screen and(min-width: $breakpoint-md) {
                max-width: $container-md;
            }
        }

        &--lg {
            @media screen and(min-width: $breakpoint-sm) {
                max-width: $container-sm;
            }

            @media screen and(min-width: $breakpoint-md) {
                max-width: $container-md;
            }

            @media screen and(min-width: $breakpoint-lg) {
                max-width: $container-lg;
            }
        }

        &--xl {
            @media screen and(min-width: $breakpoint-sm) {
                max-width: $container-sm;
            }

            @media screen and(min-width: $breakpoint-md) {
                max-width: $container-md;
            }

            @media screen and(min-width: $breakpoint-lg) {
                max-width: $container-lg;
            }

            @media screen and(min-width: $breakpoint-xl) {
                max-width: $container-xl;
            }
        }

    }

    &-section {
        padding: $padding-section/2 0;

        @media screen and(min-width: $breakpoint-md) {
            padding: $padding-section 0;
        }

        &--primary {
            color: $color-white;
            background: $color-primary;
        }

        &--secondary {
            color: $color-white;
            background: $color-secondary;
        }
    }

    &-is-selected {
        color: $color-third;
        border-bottom: 2px solid $color-third;
        padding-bottom: .4rem;
    }
}
</style>
