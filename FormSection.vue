<template>
    <form @submit.prevent="$emit('submitted')">
        <slot></slot>
    </form>
</template>

<script>
    import JetSectionTitle from './SectionTitle'

    export default {
        components: {
            JetSectionTitle,
        },

        computed: {
            hasActions() {
                return !! this.$slots.actions
            }
        }
    }
</script>
