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
        <tr v-for="meeting in meetings" :key="meeting.name">
            <td>{{ meeting.name }}</td>
            <td>{{ meeting.description }}</td>
            <participants-list :username="username"></participants-list>
        </tr>
        </tbody>
    </table>
    <table v-else>
        <h5>Brak zaplanowanych spotkan.</h5>
    </table>
</template>

<script>
    import ParticipantsList from "./ParticipantsList";

    export default {
        components: {ParticipantsList},
        props: ['username', 'meetings']
    }
</script>