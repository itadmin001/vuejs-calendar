<template>
    <div id="event-form" :class="{active: active}" :style="{top: top, left: left}">
        <h4>Add an Event</h4>
        <div class="text">
            <input type="text" v-model="description"/>
        </div>
        <div class="buttons">
            <button @click="create">Create</button>
        </div>
        <button id="close-button" @click="close">&#10005</button>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                description: ''
            }
        },
        methods: {
            close() {
                this.$store.commit('eventFormActive', false);
            },
            create() {
                this.$store.commit('addEvent', this.description);
            }
        },
        computed:{
            active() {
                return this.$store.state.eventFormActive;
            },
            top() {
                return `${this.$store.state.eventFormPosY}px`;
            },
            left() {
                return `${this.$store.state.eventFormPosX}px`;
            }
        }
    }
</script>
