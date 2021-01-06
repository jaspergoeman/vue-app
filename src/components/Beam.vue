<script>
import subgroups from "../assets/data/subgroups.json";
import topics from "../assets/data/topics.json";

export default {
    name: 'Beam',
    
    data: () => {
        return {
            selectedTopic: "",
            selectedSubgroup: "",
            showInput: false,
            subgroups: subgroups,
            topics: topics,
        }
    },
    methods: {
        setTopic: function (topic) {
            this.selectedTopic = topic;
            this.$emit('setTopic', this.selectedTopic);
            this.showInput= false;
        },
        setSubgroup: function (subgroup) {
            this.selectedSubgroup = subgroup;
            this.$emit('setSubgroup', this.selectedSubgroup);
            this.showInput= false;
        }
    },
    
}
</script>
<template>
<div>
    <section class="App-section App-section--primary">
        <div class="App-container App-container--xl">
            <div class="beam">
                <ul>
                   <li v-for="subgroup in subgroups" :key="subgroup.name">
                        <a v-bind:class="[selectedSubgroup === subgroup.name ? 'beam__isSelected' :'']" v-on:click="setSubgroup(subgroup.name)">{{subgroup.name}}</a>
                    </li>
                    <div class="beam__div-item">
                        <input v-if="showInput" class="beam__input" type="text"  placeholder="zoekterm" />
                        <div class="clickable beam__search">
                            <i class="fas fa-search"  v-on:mouseover="showInput = true"></i>
                        </div>

                    </div>
                </ul>

            </div>
        </div>
    </section>
    <section class="App-section App-section--secondary">
        <div class="App-container App-container--xl">
            <div class="beam">
                <ul>
                    <li v-for="topic in topics" :key="topic.name">
                        <a v-bind:class="[selectedTopic === topic.name ? 'beam__isSelected' : '' ]" v-on:click="setTopic(topic.name)">{{topic.name}}</a>
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

    &__isSelected {
        text-decoration: overline;

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
