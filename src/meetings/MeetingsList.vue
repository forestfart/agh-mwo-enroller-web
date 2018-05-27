<template>
    <div>
        <h4 v-if="meetings.length > 0">Zaplanowane zajecia ({{ meetings.length }})</h4>
        <table v-if="meetings.length > 0">
            <thead>
            <tr>
                <th>Nazwa spotkania</th>
                <th>Opis</th>
                <th>Uczestnicy</th>
                <th></th>
            </tr>
            </thead>
            <tbody>
                <tr v-for="(meeting, meetingId) in meetings" :key="meetingId">
                    <td>{{ meeting.name }}</td>
                    <td>{{ meeting.description }}</td>
                    <td>
                        <list v-for="participant in meeting.participants" :key="participant">&#9758; {{ participant }}<br /></list>
                    </td>
                    <td>
                        <div class="float-right">
                            <button @click="modifyParticipants(meetingId)" class="button button-outline">{{ buttonLabelToDisplay(meetingId) }}</button>
                            <button v-if="meeting.participants.length < 1" @click="removeMeeting(meetingId)">usun puste spotkanie</button>
                        </div>
                    </td>
                </tr>
            </tbody>
        </table>
        <table v-else>
            <h5>Brak zaplanowanych spotkan.</h5>
        </table>
    </div>
</template>

<script>
    export default {
        props: ['username', 'meetings', 'buttonLabel'],
        methods: {
            modifyParticipants: function(meetingId) {
                this.$emit('modifyParticipants', meetingId)
            },
            removeMeeting: function (meetingId) {
                this.$emit('removeMeeting', meetingId);
            },
            buttonLabelToDisplay: function(meetingId) {
                if (this.meetings[meetingId].participants.includes(this.username)) {
                    return "wypisz sie";
                } else {
                    return "zapisz sie";
                }
            }
        }
    }
</script>