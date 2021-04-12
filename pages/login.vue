<template>
  <div>
  <b-card>
      <b-card-header>
          <h1>login</h1>
      </b-card-header>
      <b-card-body>
          <b-row>
              <b-col md="6">
                  <label for="">email</label>
                  <b-form-input placeholder="Enter your email"></b-form-input>
                  <label for="">password</label>
                  <b-form-input placeholder="Enter your password" type="password"></b-form-input>
              </b-col>
          </b-row>
          <b-row>
              <b-col md="6" class="btn">
                   <b-button variant="primary">login</b-button>
                   <b-button variant="danger">register</b-button>
              </b-col>
          </b-row>
      </b-card-body>
  </b-card>
  </div>
</template>

<script>
export default {
  name: "Login",
};
</script>
<style scoped>

</style>
