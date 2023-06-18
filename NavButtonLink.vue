<template>
    <inertia-link :href="href" :class="classes">
        <slot></slot>
    </inertia-link>
</template>

<script>
export default {
    props: ['href', 'active', 'type'],

    computed: {
        classes() {

            if(this.type == 'red') {
                return 'flex justify-between items-center py-2 border-radius-xl px-4 bg-red-500 text-sm rounded text-gray-100 cursor-pointer hover:bg-red-600 hover:text-gray-100 focus:outline-none';
            }

            return this.active
                ? 'flex justify-between items-center py-2 border-radius-xl px-4 bg-indigo-500 text-sm rounded text-gray-100 cursor-pointer hover:bg-indigo-600 hover:text-gray-100 focus:outline-none'
                : 'flex justify-between items-center py-2 border-radius-xl px-4 bg-indigo-500 text-sm rounded text-gray-100 cursor-pointer hover:bg-indigo-600 hover:text-gray-100 focus:outline-none'
        }
    }
}
</script>
