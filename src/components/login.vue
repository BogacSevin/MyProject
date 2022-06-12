<template>
  <div style="
  margin-left: auto;
  margin-right: auto;
  width: 50em;
  height: 50rem;
  margin-top: 15%;
  text-align: left;">
    <b-form @submit.prevent="onCreatePost" @submit="onSubmit" @reset="onReset" v-if="show">
      <b-form-group
        id="input-group-1"
        label="Email address:"
        label-for="input-1"
        description="We'll never share your email with anyone else."
      >
        <b-form-input
          id="input-1"
          v-model="form.email"
          type="email"
          placeholder="Enter email"
          required
        ></b-form-input>
      </b-form-group>
      <b-form-group id="input-group-2" label="Your Password:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.password"
          placeholder="Enter password"
          required
          type="password"
        ></b-form-input>
      </b-form-group>
          <label class="mt-2" @click="$bvModal.show('bv-modal-example')"> Şifremi Unuttum? </label>
  <b-modal id="bv-modal-example" hide-footer>
    <div>
  <b-form inline>
    <label class="sr-only" for="inline-form-input-username">Email</label>
    <b-input-group  class="mb-2 mr-sm-2 mb-sm-0">
      <b-form-input id="inline-form-input-username" placeholder="Email"></b-form-input>
    </b-input-group>
    <b-button variant="primary" class="mt-4" block @click="$bvModal.hide('bv-modal-example')" >Şifremi Yenile</b-button>
  </b-form>
</div>
  </b-modal>       
        <div style="margin-top:2rem; ">
      <b-button type="submit" style="padding-rigt:0.5rem;" variant="primary">Submit</b-button>
        </div>
    </b-form>
  </div>
</template>
    <!-- <b-button class="mt-3" block @click="$bvModal.hide('bv-modal-example')">Close Me</b-button> -->
<script>
import axios from 'axios';
  export default {
    data() {
      return {
        form: {
          email: 'fintechtestuser@yandex.com',
          password: '99Salman99*',
          LoginType: '50dcd869-eeb3-ec11-ac1f-000c29330757'
        },
        show: true,
      }
    },
    methods: {
      onCreatePost(){
        let formData = new FormData();
        formData.append('Email', this.form.email);
        formData.append('Password', this.form.password);
        formData.append('LoginType', this.form.LoginType);

        axios
        .post(
          'https://dev-smoothie-api.fintechyazilim.com/api/User/Login',
          formData
        ).then(response => {
          console.log(response);
        }).catch((error) => {
          console.log(error)
        })
      },
      onSubmit(event) {
        event.preventDefault()
        // alert(JSON.stringify(this.form))
      },
      onReset(event) {
        event.preventDefault()
        // Reset our form values
        this.form.email = ''
        this.form.password = ''
      }
    }
  }
</script>