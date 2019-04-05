<template>
  <div>
	<!-- Login Form -->
	<!-- /Login Form -->
  </div>
</template>

<script>
import firebase from 'firebase'

export default {
  name: 'Login',
	data() {
		return {
            email: null,
            password: null,
            feedback: null
		}
	},
	methods: {
		login(){
            // Check if the email and password are still null
            if(this.email && this.password){
                // ASYNC call that sends email and password
                firebase.auth().signInWithEmailAndPassword(this.email, this.password)
                // Success
                .then(user => {
                    // Do something (Redirect with $router)
                    console.log(user)
                }).catch(err => {
                    // Error
                    this.feedback = err.message
                })
            } else {
                // Email or password is empty
                this.feedback = 'Please fill in both fields'
            }
        }
	}
}
</script>

<style></style>
