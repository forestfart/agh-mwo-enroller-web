<template>
    <table v-if="meetings.length > 0">
        <thead>
        <tr>
            <th width=25%> Nazwa spotkania</th>
            <th width=25%>Opis</th>
            <th widht=50%>Uczestnicy</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="(meeting, meetingId) in meetings" :key="meetingId">
            <td>{{ meeting.name }}</td>
            <td>{{ meeting.description }}</td>
            <td><list v-for="participant in meeting.participants">&#9758; {{ participant }}<br /></list></td>
            <td><button @click="addNewParticipant(meetingId)">add</button></td>
            <td v-if="meeting.participants.length < 1"><button @click="removeMeeting(meetingId)">Usun puste spotkanie</button></td>
        </tr>
        </tbody>
    </table>
    <table v-else>
        <h5>Brak zaplanowanych spotkan.</h5>
    </table>
</template>

<script>
    export default {
        props: ['username', 'meetings'],
        methods: {
            addNewParticipant: function(meetingId) {
                this.$emit('addParticipant', meetingId)
            },
            removeMeeting: function (meetingId) {
                this.$emit('removeMeeting', meetingId);
            }
        }
    }
</script>