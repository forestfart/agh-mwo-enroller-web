<template>
<div>
    <h2>Zajęcia</h2>
    <new-meeting-form @added="addNewMeeting($event)" :side-warning=noMeetingNameMessage></new-meeting-form>
    <meetings-list v-on:removeMeeting="removeMeeting" :username="username" :meetings="meetings"></meetings-list>
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
                noMeetingNameMessage: ''
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
            },
            removeMeeting: function (index) {
                this.meetings.splice(index, 1);
            }
        }
    }
</script>