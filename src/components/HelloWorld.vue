<!-- src/components/HelloDecorator.vue -->
<!-- This is an alternative way to define the Hello component using decorators -->
<template>
    <div class="container col-6">
        <input type="number" v-model="enthusiasm" class="form-control">
        <div class="greeting">Hello {{name}}{{exclamationMarks}}</div>
        <button @click="decrement" class="btn btn-danger">-</button>
        <button @click="increment" class="btn btn-success">+</button>

        <hr>

        <input type="text" v-model="username"  class="form-control">
        <input type="password" v-model="password"  class="form-control">
        <button class="btn btn-success" @click="login">Login</button>
    </div>
</template>

<script lang="ts">
    import { Vue, Component, Prop } from "vue-property-decorator";

    @Component
    export default class HelloDecorator extends Vue {
        @Prop() name!: string;
        @Prop() initialEnthusiasm!: number;

        enthusiasm = this.initialEnthusiasm;

        username: string = '';
        password: string = '';

        increment() {
            this.enthusiasm++;
        }
        decrement() {
            if (this.enthusiasm > 1) {
                this.enthusiasm--;
            }
        }

        get exclamationMarks(): string {
            return Array(this.enthusiasm + 1).join('!');
        }

        login () {
            console.log(this.username, this.password)
        }
    }
</script>

<style>
    .greeting {
        font-size: 20px;
    }
</style>