<template>
    <div>
	    <!-- Logout is usually a link or button sitting in another component -->
    </div>
</template>

<script>
import firebase from 'firebase'

export default {
    name: 'Logout',
	data() {
		return {
		}
	},
	methods: {
		logout(){
            firebase.auth.signOut.then(() => {
                this.$router.push({ name: 'Signup' })
            })
        }
	}
}
</script>