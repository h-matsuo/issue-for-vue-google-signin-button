<template>
  <div>
    <GSignInButton
      :params="googleSignInParams"
      @success="onSignInSuccess"
      @error="onSignInError"
    >
      Sign in with Google
    </GSignInButton>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component({
  components: {
    GSignInButton: () => import('vue-google-signin-button')
  }
})
export default class Page extends Vue {

  googleSignInParams = {
    client_id: 'YOUR_APP_CLIENT_ID.apps.googleusercontent.com'
  }

  head() {
    return {
      script: [
        {
          src: 'https://apis.google.com/js/api:client.js'
        }
      ]
    }
  }

  onSignInSuccess(googleUser) {
    console.log(googleUser)
  }

  onSignInError(error) {
    console.error(error)
  }
}
</script>

<style scoped>
.g-signin-button {
  /* This is where you control how the button looks. Be creative! */
  display: inline-block;
  padding: 4px 8px;
  border-radius: 3px;
  background-color: #3c82f7;
  color: #fff;
  box-shadow: 0 3px 0 #0f69ff;
}
</style>
