<template>
    <div class="container">
        <div class="col-6 offset-3 bg-dark p-4">
            <div class="row">
                <div class="col">
                    <div class="form-group">
                        <input type="number" :value="value" readonly class="form-control-lg form-control">
                    </div>
                </div>
            </div>
            <app-key-row v-for="(keyRow, index) in keys" :key="index" :keyRow="keyRow" @input="calculate"></app-key-row>
            <div class="row mb-4">
                <div class="col-9 text-center">
                    <button class="btn btn-lg btn-light btn-block" type="button" @click="calculate(0)">0</button>
                </div>
                <div class="col text-center">
                    <button class="btn btn-lg btn-light btn-block" type="button" @click="calculate('/')">/</button>
                </div>
            </div>
            <div class="row mb-4">
                <div class="col-3 offset-6 text-center">
                    <button class="btn btn-lg btn-danger btn-block" type="button" @click="calculate('clear')">Clear</button>
                </div>
                <div class="col-3 text-center">
                    <button class="btn btn-lg btn-primary btn-block" type="button" @click="calculate('=')">=</button>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
import KeyRow from './KeyRow.vue';
export default {
    components: {
        appKeyRow: KeyRow
    },
    data() {
        return {
            value: 0,
            keys: [
                [9, 8, 7, '+'],
                [6, 5, 4, '-'],
                [3, 2, 1, 'x'],
            ]
        }
    },
    methods: {
        calculate(value) {
            if(isNaN(value))
            {
                if(value == 'clear')
                {
                    console.log('cleared');
                    this.value = 0;
                }


                console.log("Action")
            }
            else
            {
                console.log("Number")

                let newValue = "";
                newValue += this.value + "" + value;
                this.value = parseFloat(newValue);
            }
        }
    }
}
</script>

<style>
    @import url('https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css');

    body {
        padding: 20px 0px;
    }
</style>
