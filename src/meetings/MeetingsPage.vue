<template>
<div>
    <h2>Zajęcia</h2>
    <button v-show="!activeAddMeetingPanel" @click="showAddMeetingPanel">dodaj nowe spotkanie</button>
    <new-meeting-form v-show="activeAddMeetingPanel" @added="addNewMeeting($event)" :side-warning=noMeetingNameMessage></new-meeting-form>
    <meetings-list @modifyParticipants="modifyParticipants($event)" @removeMeeting="removeMeeting" :username="username" :meetings="meetings"></meetings-list>
</div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";

    export default {
        props: ['username'],
        components: {NewMeetingForm, MeetingsList},
        data() {
            return {
                meetings: [],
                noMeetingNameMessage: '',
                activeAddMeetingPanel: false
            };
        },
        methods: {
            addNewMeeting(meeting) {
                if (meeting.name) {
                    this.meetings.push(meeting);
                    this.noMeetingNameMessage = '';
                } else {
                    this.noMeetingNameMessage = 'Spotkanie musi miec nazwe!';
                }
                this.activeAddMeetingPanel = false;
            },
            modifyParticipants(meetingId) {
                if (this.meetings[meetingId].participants.includes(this.username)) {
                    this.meetings[meetingId].participants.pop(this.username);
                } else {
                    this.meetings[meetingId].participants.push(this.username);
                };
            },
            removeMeeting: function (meetingId) {
                this.meetings.splice(meetingId, 1);
            },
            showAddMeetingPanel() {
                this.activeAddMeetingPanel = true;
            }
        }
    }
</script>