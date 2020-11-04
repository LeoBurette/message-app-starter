<template>
    <div class="messages">
        <h2>This is the messages</h2>
        <message v-on:id="updateRead" v-for="mess in message" :key="mess.id" :message="mess"/>
    </div>
</template>

<script>
    import Message from "./Message";
    import {messagesMock} from "../mocks/messages.mock";

    export default {
        name: "Messages",
        beforeMount() {
            this.countUnread();
        },
        data(){
            return {
                message: messagesMock,
            };
        },
        created() {
            this.sortMessagesByDate();
        },
        components:{
            Message,
        },
        methods:{
            updateRead(id){
                this.message.find(mess => mess.id === id).read = true;
                this.countUnread();
            },
            sortMessagesByDate(){
                console.log(this.message[0].date.split(" ")[4]);
                this.message.sort((a,b) => -a.date.localeCompare(b.date));
            },
            countUnread(){
                var i = 0;
                this.message.forEach(e => {
                    if(e.read === false){
                        i = i + 1;
                    }
                });
                this.$emit("unread",i);
            }
        }
    }
</script>

<style scoped>
    .messages{
        border: solid 1px red;
    }
</style>
