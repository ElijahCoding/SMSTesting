<template>
    <div class="container">
        <div class="row mt-5">
            <div class="col-md-12">
                <form @submit.prevent="submit">
                    <div class="form-group">
                        <textarea name="name"
                                  class="form-control"
                                  required
                                  placeholder="Token"
                                  >
                        </textarea>
                    </div>

                    <div class="form-group">
                        <input type="text"
                               required
                               class="form-control"
                               placeholder="ID"
                               >
                    </div>

                    <div class="form-group">
                        <input type="text"
                               required
                               class="form-control"
                               placeholder="FirstName"
                               >
                    </div>

                    <div class="form-group">
                        <input type="text"
                               required
                               class="form-control"
                               placeholder="LastName"
                               >
                    </div>

                    <div class="form-group">
                        <input type="email"
                               required
                               class="form-control"
                               placeholder="Email"
                               >
                    </div>

                    <div class="text-center">
                        <button type="submit" class="btn btn-dark">
                            Submit
                        </button>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>


<script>
    export default {

    }
</script>
