<template>
    <div>
        <td width="100%"><tr v-for="participant in participants" :key="username">o {{ participant }}</tr></td>
        <td width="100%" valign="middle"><button class="float-right" @click="addNewParticipant">add</button></td>
    </div>
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

