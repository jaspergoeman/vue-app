<script>
export default {
    name: 'Beam',
    props: {
        topics: {
            type: Array
        },
        subgroups: {
            type: Array
        }
    },
    data: () => {
        return {
            selectedTopic: "",
            selectedSubgroup: ""
        }
    },
    methods: {
        setTopic: function (topic) {
            this.selectedTopic = topic;
            this.$emit('setTopic', this.selectedTopic);
        },
        setSubgroup: function (subgroup) {
            this.selectedSubgroup = subgroup;
            this.$emit('setSubgroup', this.selectedSubgroup);
        }
    }
}
</script>
<template>
<div>
    <section className="App-section App-section--primary">
        <div className="App-container App-container--xl">
            <div className="beam">
                <ul>
                    <li v-for="subgroup in subgroups" :key="subgroup">
                        <a v-bind:class="[selectedSubgroup === subgroup ? 'beam__isSelected' :'']" v-on:click="setSubgroup(subgroup)">{{subgroup}}</a>
                    </li>
                    <div className="beam__div-item">
                        <input className="beam__input" type="text" placeholder="zoekterm" />
                        <div className="clickable beam__search">
                            <i class="fas fa-search"></i>
                        </div>

                    </div>
                </ul>

            </div>
        </div>
    </section>
    <section className="App-section App-section--secondary">
        <div className="App-container App-container--xl">
            <div className="beam">
                <ul>
                    <li v-for="topic in topics" :key="topic">
                        <a v-bind:class="[selectedTopic === topic ? 'beam__isSelected' :'']" v-on:click="setTopic(topic)">{{topic}}</a>
                    </li>
                </ul>
            </div>
        </div>
    </section>
</div>
</template>

<style lang="scss" scoped>
@import '../scss/Variables.scss';

.beam {
    text-transform: uppercase;
    font-weight: $font-weight-semibold;

    ul {
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        justify-content: space-around;

        li {
            margin-right: .4rem;
            margin-bottom: .8rem;
            font-size: .8rem;

            a {
                color: white;
            }

        }
    }

    &__subgroup__isSelected {
        a {
            text-decoration: overline;
        }
    }

    &__topic__isSelected {
        a {
            text-decoration: overline;
        }
    }

    &__div-item {
        display: flex;
    }

    &__input {
        display: flex;
        background: transparent;
        color: $color-white;
        border: none;
        border-bottom: 3px solid $color-third;
        color: $color-white;
        margin-top: -.6rem;
        margin-right: .6rem;

        &--show {
            display: flex;
        }
    }

    &__input:focus {
        outline: none;
    }

    &__input::placeholder {
        color: $color-white;
    }

}
</style>
