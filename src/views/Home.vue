<template>
    <div class="container">
        <div class="row mt-5">
            <div class="col-md-12">
                <form @submit.prevent="submit">
                        <div class="form-group">
                            <vue-tel-input v-model="form.phone"
                                           required
                                           class="form-control"
                                           defaultCountry="ru"
                                           :preferredCountries="['us', 'gb', 'ru']">
                                           >
                            </vue-tel-input>
                        </div>

                        <div class="form-group">
                            <input type="text"
                                   class="form-control"
                                   placeholder="Name"
                                   v-model="form.name"
                                   >
                        </div>

                        <div class="form-group">
                            <textarea rows="8"
                                      class="form-control"
                                      cols="80"
                                      v-model="form.text"
                                      ></textarea>
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
                form: {
                    name: '',
                    phone: '',
                    text: ''
                }
            }
        },

        components: {
            VueTelInput
        },

        methods: {
            submit () {
                let phone = this.form.phone.replace(/\s/g, '').replace('+', '')

                axios({
                    method: 'post',
                    url: 'https://9qmry.api.infobip.com/sms/2/text/single',
                    data: {
                        "from": this.form.name,
                        "to": this.form.phone,
                        "text": 'From ' + this.form.name + ' \n' + 'Message: ' + this.form.text
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
                    this.form = {}
                })
            }
        }

    }
</script>
