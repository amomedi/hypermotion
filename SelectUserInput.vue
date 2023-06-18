<template>
    <div class="filter-block">
        <label v-if="label" class="form-label" :for="id">{{ label }}:</label>
        <select :id="id" ref="input" v-model="selected" v-bind="$attrs" class="border-gray-200 focus:border-gray-300 focus:ring focus:ring-gray-200 focus:ring-opacity-10 rounded shadow-none mt-2 block w-full" :class="{ error: error }">
            <slot />
        </select>
        <div v-if="error" class="form-error text-red-400">{{ error }}</div>
    </div>
</template>

<script>
export default {
    inheritAttrs: false,
    props: {
        id: {
            type: String,
            default() {
                return `select-input-${this._uid}`
            },
        },
        value: [String, Number, Boolean, Object],
        label: String,
        error: String,
    },
    data() {
        return {
            selected: this.value,
        }
    },
    watch: {
        selected(selected) {
            this.$emit('input', selected)
        },
    },
    methods: {
        focus() {
            this.$refs.input.focus()
        },
        select() {
            this.$refs.input.select()
        },
    },
}
</script>
