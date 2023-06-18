<template>
    <inertia-link :href="href" :class="classes">
        <slot></slot>
    </inertia-link>
</template>

<script>
    export default {
        props: ['href', 'active'],

        computed: {
            classes() {
                return this.active
                            ? 'w-full flex justify-between items-center py-3 px-6 text-gray-100 cursor-pointer bg-gray-700 text-gray-100 focus:outline-none'
                            : 'w-full flex justify-between items-center py-3 px-6 text-gray-100 cursor-pointer hover:bg-gray-700 hover:text-gray-100 focus:outline-none'
            }
        }
    }
</script>
