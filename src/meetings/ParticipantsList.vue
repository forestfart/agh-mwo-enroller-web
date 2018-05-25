<template>
    <tbody v-if="participants.length > 0">
        <tr v-for="participant in participants" :key="username">
            o {{ participant }}
        </tr>
        <button v-if="participants" class="float-right" @click="addNewParticipant">add</button>
    </tbody>
    <tbody v-else>
        <button v-if="participants" class="float-right" @click="addNewParticipant">add</button>
    </tbody>
</template>

<script>
    export default {
        props: ['username'],
        data() {
            return {
                participants: [],
                email: ''
            }
        },
        methods: {
            addNewParticipant() {
                this.participants.push(this.username);
            }
        }
    }
</script>