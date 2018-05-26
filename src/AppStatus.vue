<template>
   <div>
        <h2>Witaj {{ username }}!
            <div class="float-right">
                <button class="button button-outline" @click="enter()">{{ buttonLabelToDisplay }}</button>
            </div>
        </h2>
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
            return this.buttonLabel || 'Wyloguj';
        }
    }
}
</script>