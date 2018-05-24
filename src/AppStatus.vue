<template>
   <div>
        <label>Witaj {{ username }}! <button @click="enter()">{{ buttonLabelToDisplay }}</button></label>
   </div>
</template>

<script>
export default {
    props: ['buttonLabel', 'username'],
    data() {
        return {
            email: '',
        }
    },
    methods: {
        enter() {
            this.$emit('login', this.email);
        }
    },
    computed: {
        buttonLabelToDisplay() {
            return this.buttonLabel || 'Wyloguj się';
        }
    }
}
</script>