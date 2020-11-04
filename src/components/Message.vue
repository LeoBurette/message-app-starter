<template>
    <div class="message">
        <div class="contact">
            <img :src="message.sender.profileImage"/>
            <p class="name">
                {{message.sender.name}}
            </p>
        </div>
        <div>
            <b v-if="!message.read">
                {{message.content}} {{this.date()}}
            </b>
            <p v-if="message.read">
                {{message.content}} {{this.date()}}
            </p>
        </div>
        <button v-on:click="markAsRead()">Mark as read</button>
    </div>
</template>

<script>
    export default {
        name: "Message",
        props: {
            message: Object,
        },
        methods:{
            markAsRead(){
                this.$emit("id",this.message.id);
            },
            date(){
                var recup = this.message.date.split(' ');
                return recup[4];
            }
        }
    }
</script>

<style scoped>
    .message{
        border: solid 1px blue;
    }
</style>
