<template>
    <transition name="modal-content" mode="out-in">
        <keep-alive>
            <component @disableForm = "modalDisableForm"
                    @switch="currentComponent==='login-component' ? currentComponent='reg-component' : currentComponent='login-component'"
                    :is="currentComponent"></component>

        </keep-alive>
    </transition>
</template>

<script>
    import ModalAuthorizationLogin from "@/components/ModalAuthorizationLogin";
    import ModalAuthorizationRegistration from "@/components/ModalAuthorizationRegistration";
    import Modal from "@/components/Modal";

    export default {
        name: "ModalAuthorization",
        components: {
            Modal,
            'login-component': ModalAuthorizationLogin,
            'reg-component': ModalAuthorizationRegistration
        },
        data() {
            return {
                currentComponent: 'login-component'
            }
        },
        methods: {
            modalDisableForm: function (state) {
                this.$emit('disableForm', state)
            }
        }

    }
</script>


<style lang="sass" scoped>
    @import "../variables"
</style>
