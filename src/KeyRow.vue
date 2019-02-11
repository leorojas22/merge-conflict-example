<template>
    <div class="row mb-4">
        <div class="col text-center" v-for="key in keyRow" :key="key">
            <button class="btn btn-lg btn-light btn-block" @click="buttonClicked(key)" type="button">{{ key }}</button>
        </div>
    </div>
</template>

<script>
export default {
    props: [
        'keyRow'
    ],
    methods: {
        buttonClicked(value) {
            this.$emit("input", value);
        }
    }
}
</script>

