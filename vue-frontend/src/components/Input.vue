<template>
    <div class="form">
        <h2>Form</h2>
        <div class="input-box">
            Name: <input class="input" v-model="input" placeholder="Enter a show name!"/>
        </div>
        <div>
             <button class="button" v-on:click="createShow" type="button"> Add show</button>
        </div>
    </div>
</template>

<script>
import {eventBus} from "@/eventBus"
export default {
    data() {
        return {
            input: ""
        }
    },
    methods: {
        createShow() {
            eventBus.$emit("createShow", this.input);
            this.input = "";
        }
    }
}
</script>

<style scoped>
.form {
    margin: 2rem;
    background: #41B883;
}
h2 {
    color: #34495E;
}
.input-box {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0.8rem;
    padding: 0.8rem;
}
.input {
    margin-left: 0.8rem;
}
</style>