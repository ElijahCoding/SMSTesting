<template>
    <div class="container">
        <div class="row mt-5">
            <div class="col-md-12">
                <form @submit.prevent="submit">
                        <div class="form-group">
                            <vue-tel-input v-model="phone"
                                           class="form-control"
                                           :preferredCountries="['us', 'gb', 'ru']">
                                           >
                            </vue-tel-input>

                        </div>

                        <div class="text-center">
                            <button type="submit" class="btn btn-dark">
                                Send
                            </button>
                        </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
    import 'vue-tel-input/dist/vue-tel-input.css'
    import VueTelInput from 'vue-tel-input'

    export default {
        data () {
            return {
                phone: ''
            }
        },

        components: {
            VueTelInput
        },

        methods: {
            submit () {
                console.log(this.phone);
            }
        }

    }
</script>
