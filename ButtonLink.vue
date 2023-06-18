<template>
    <button v-bind="$attrs" :class="classes">
        <slot></slot>
    </button>
</template>

<script>
export default {
    props: ['type'],

    computed: {
        classes() {

            let typeClass;

            if(this.type == 'red') {
                typeClass = 'bg-red-500 hover:bg-red-600 ';
            }

            if(this.type == 'green') {
                typeClass = 'bg-green-500 hover:bg-green-600 ';
            }

            if(this.type == 'indigo') {
                typeClass = 'bg-indigo-500 hover:bg-indigo-600 ';
            }

            return 'flex justify-between items-center py-2 border-radius-xl px-4 cursor-pointer text-sm rounded text-gray-100 hover:text-gray-100 focus:outline-none ' + typeClass;
        }
    }
}
</script>
