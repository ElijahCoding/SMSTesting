<template>
    <div class="container">
        <div class="row mt-5">
            <div class="col-md-12">
                <form @submit.prevent="submit">
                        <div class="form-group">
                            <vue-tel-input v-model="phone"
                                           required
                                           class="form-control"
                                           defaultCountry="ru"
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
                let phone = this.phone.replace(/\s/g, '').replace('+', '')

                axios({
                    method: 'post',
                    url: 'https://9qmry.api.infobip.com/sms/2/text/single',
                    data: {
                        "from": "InfoSMS",
                        "to": phone,
                        "text": `Test SMS from ${phone}`
                    },
                    headers: {
                        'Content-Type': 'application/json',
                        'Accept': 'application/json'
                    },
                    auth: {
                        username: 'Bitchange123',
                        password: 'QwertY7747'
                    }
                }).then(response => {
                    this.phone = ''
                })
            }
        }

    }
</script>
