<template>
  <div>
	<!-- Signup Form -->
	<!-- /Signup Form -->
  </div>
</template>

<script>
import slugify from 'slugify'
import db from '@/firebase/init'
import firebase from 'firebase'

export default {
  name: 'Signup',
	data() {
		return {
            email: null,
            password: null,
            username: null,
            feedback: null,
            slug: null
		}
	},
	methods: {
		signup(){
            if(this.username){
                this.slug = slugify(this.username, {
                    replacement: '-',
                    remove: /[$*_+~.()'"!\-:@]/g,
                    lower: true
                })
                let ref = db.collection('users').doc(this.slug)
                ref.get().then(doc => {
                    if(doc.exists){
                        this.feedack = 'This username already exists'
                    } else {
                        firebase.auth().createUserWithEmailAndPassword(this.email, this.password)
                        .catch(err => {
                            console.log(err)
                            this.feedback = err.message
                        })
                    }
                })
            } else {
                this.feedback = 'You must enter a username'
            }
        }
	}
}
</script>

<style></style>