<template>
    <tbody v-if="participants.length > 0">
        <tr v-for="participant in participants" :key="username">
                <td>o {{ username }}</td>
        </tr>
        <div align="right">
            <button v-if="participants" class="float-right" @click="addNewParticipant">add</button>
        </div>
    </tbody>
    <tbody v-else>
            <tr>
                none
            </tr>
            <th>
                <button v-if="participants" class="float-right" @click="addNewParticipant">add</button>
            </th>
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
                this.participants.push('asd');
            }
        }
    }
</script>