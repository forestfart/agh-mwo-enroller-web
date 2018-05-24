<template>
    <table v-if="meetings.length > 0">
        <thead>
        <tr>
            <th>Nazwa spotkania</th>
            <th>Opis</th>
            <th>Uczestnicy</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="meeting in meetings" :key="meeting.name">
            <td>{{ meeting.name }}</td>
            <td>{{ meeting.description }}</td>
            <td><participants-list :username="username"></participants-list></td>
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