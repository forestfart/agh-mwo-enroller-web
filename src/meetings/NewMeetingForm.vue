<template xmlns="http://www.w3.org/1999/html">
    <form @submit.prevent="addNewMeeting()">
        <h3>Dodaj nowe spotkanie</h3>
        <label>Nazwa</label>
        <input type="text" v-model="newMeeting.name">
        <label>Opis</label>
        <textarea v-model="newMeeting.description"></textarea>
        <div id="warning"><button v-on:keyup.enter="addNewMeeting()" >Dodaj</button> {{ sideWarning }}</div>
    </form>
</template>

<script>
    export default {
        props: ['sideWarning'],
        data() {
            return {
                newMeeting: {
                    name: '',
                    description: '',
                    participants: []
                }
            };
        },
        methods: {
            addNewMeeting() {
                this.$emit('added', this.newMeeting);
                this.newMeeting = {
                    name: '',
                    description: '',
                    participants: []
                }
            }
        },
        computed: {
            noMeetingNameMessage() {
                return this.sideWarning || '';
            }
        }
    }
</script>