<template>
    <div>
        <input type="text" placeholder="nombre completo">
        <input type="text" placeholder="apellidos">
        <input type="text" v-model="email" placeholder="correo">
        <input type="text" v-model="password" placeholder="contraseña">
        <input type="text" placeholder="confirmar contraseña">
        <button @click="register()">Registrar</button>
    </div>
</template>

<script>
import { db } from '@/firebase/init.js'

export default {
  name: 'Register',
	data(){
		return{
			email: '',
			password:'',
		}
	},
	methods:{
		register(){
			db.auth().createUserWithEmailAndPassword(this.email, this.password)
				.then(()=>{
					alert('ingreso a la siguiente pagina')
					this.$router.push('/login')
				}).catch((error)=>{
					console.log(error);
					
				})
		}
	}
}
</script>