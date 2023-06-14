<template>
    <div class="msg">
        <h1>Hello fellow people</h1>
    </div>
    <div class="container">
        <div style="display: inline-block;">
            <div class="row" v-for="message in messages" :key="message.id">
                <div class="row">
                    <img src="../assets/letter-m.png" style="width: 120px; height: 90px; margin-left: 40px;" />
                    <h4>{{ message.subject }}</h4>
                    <h3>{{ message.message }}</h3>
                    <p>{{ message.display }}</p>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import messagesData from '../data/messages.json';
export default{
    data() {
        return {messages: messagesData}
    }
}
</script>
<style scoped>
.msg{
    font-size: 20px;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    font-weight: 600;
    margin-top: 80px;
}
</style>