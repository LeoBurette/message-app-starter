<template>
    <div class="menu">
        <h2>This is the menu with {{unreadMessages}} unread messages</h2>
        <i class="fas fa-users"></i><i class="fas fa-phone-alt"></i><i class="fas fa-comments"></i><i class="fas fa-ellipsis-v"></i>
    </div>
</template>

<script>
    export default {
        name: "Menu",
        props: {
            unreadMessages: Number,
        }
    }
</script>

<style scoped>
    .menu{
        border: solid 1px green;
    }
    i {
        margin-left: 10%;
    }
</style>
