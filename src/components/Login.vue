<template>
  <div class="login bg-dark">
      <div class="container py-5">
        <div class="row">
            <div class="col-md-12">
                <h2 class="text-center text-white mb-4">Aplikasi Kasir</h2>
                <div class="row">
                    <div class="col-md-6 mx-auto">
                        <!-- form card login -->
                        <div class="card rounded-0">
                            <div class="card-header">
                                <h3 class="mb-0">Login</h3>
                            </div>
                            <div class="card-body">
                                <div class="form" role="form" autocomplete="off" novalidate="">
                                    <div class="form-group">
                                        <label for="uname1">Username</label>
                                        <input type="text" class="form-control form-control-lg rounded-0" name="uname1" ref="user" required="" autofocus>
                                        <div class="invalid-feedback">Oops, kamu melupakan ini.</div>
                                    </div>
                                    <div class="form-group">
                                        <label>Password</label>
                                        <input type="password" class="form-control form-control-lg rounded-0" ref="pass" required="" autocomplete="new-password">
                                        <div class="invalid-feedback">Masukan Passwordnya juga!</div>
                                    </div>
                                    <div>
                                        <label class="custom-control custom-checkbox">
                                            <input type="checkbox" class="custom-control-input">
                                            <span class="custom-control-indicator"></span>
                                        </label>
                                    </div>
                                    <button class="btn btn-success btn-lg float-right" @click="login">Login</button>
                                </div>
                            </div>
                            <!--/card-block-->
                        </div>
                        <!-- /form card login -->
                    </div>
                </div>
                <!--/row-->
            </div>
            <!--/col-->
        </div>
        <!--/row-->
    </div>
    <!--/container-->
  </div>
</template>

<script>
import swal from 'sweetalert'
import axios from 'axios'
export default {
    name: 'login',
  data () {
      return {
        hasLogin: false
      }
  },
  methods: {
      login() {
          if(this.$refs.user.value == '') swal('Oops..', 'Silahkan periksa username anda', 'warning')
          else if(this.$refs.pass.value == '') swal('Oops..', 'Silahkan periksa password anda', 'warning')
          else {
              console.log('test')
            axios.post('https://reco-saw.herokuapp.com/login', {
                  username: this.$refs.user.value,
                  password: this.$refs.pass.value
              }).then(response => {
                  console.log(response.data)
                  swal('Selamat', `${response.data.data.display_name}`, 'success')
              }).catch(err => {
              })
          }
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
    
</style>
