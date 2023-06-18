<template>
    <span v-bind:class="{ 'bg-green-400': type == 'green', 'bg-red-400': type == 'red', 'bg-gray-500': type == 'gray', 'bg-indigo-500': type == 'indigo', 'bg-yellow-600': type == 'orange' }" class="inline-flex items-center justify-center px-2 py-1 text-xs font-bold leading-none text-white rounded">
        <slot></slot>
    </span>
</template>

<script>
export default {
    props: {
        type: {
            type: String,
        },
    }
}
</script>
