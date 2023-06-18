<template>
    <div>
        <label v-if="label" class="form-label" :for="id">{{ label }}:</label>
        <input :id="id" ref="input" v-bind="$attrs" class="border-gray-200 focus:border-gray-300 focus:ring focus:ring-gray-200 focus:ring-opacity-10 rounded mt-2 block w-full" :class="{ error: error }" :type="type" :value="value" @input="$emit('input', $event.target.value)">
        <div v-if="error" class="form-error text-red-400 mt-2">{{ error }}</div>
    </div>
</template>

<script>
export default {
    inheritAttrs: false,
    props: {
        id: {
            type: String,
            default() {
                return `text-input-${this._uid}`
            },
        },
        type: {
            type: String,
            default: 'text',
        },
        value: [Number, String],
        label: String,
        error: String,
    },
    methods: {
        focus() {
            this.$refs.input.focus()
        },
        select() {
            this.$refs.input.select()
        },
        setSelectionRange(start, end) {
            this.$refs.input.setSelectionRange(start, end)
        },
    },
}
</script>
