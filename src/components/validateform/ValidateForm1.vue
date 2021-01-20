<template>
    <form class="validate-form-container">
        <slot name="default"></slot>
        <div class="submit-area" @click.prevent="submitForm">
            <slot name="submit">
                <button class="btn btn-primary">
                    送信
                </button>
            </slot>
        </div>
    </form>
</template>

<script lang="ts">
    import {defineComponent} from 'vue'
    export default defineComponent ({
        name: "ValidateForm1",
        emits: ['form-submit'],
        setup(props, context) {
            const submitForm = () => {
                context.emit('form-submit', true)
            }

            return {
                submitForm
            }
        }
    })
</script>

<style scoped>

</style>
