<template>

	<div id="html-principal">
	
		<main class="main">
			
			<section class="sec">
				
				<form  class="form">
					
					<div class="A-titulos">
			
						<h1 class="titulo">Listas de alunos do vnw</h1>
						<h2 class="subtitulo">modulo 2</h2>
					
					</div>
					
					<div class="B-usuario">
					
						<label>Ordenar por:</label>
					
						<select class="form-control" v-model="configs.orderBy">
        				
        					<option value="name">Nome</option>				
        					<option value="age">Idade</option>
					
					</select>
					
					</div>
					
					<div class="C-resente">
						
						<label>Orderm:</label>
					    
					    <select class="form-control" v-model="configs.order">
					        
					        <option value="asc">Crescente</option>
					        <option value="desc">Decrescente</option> 
					
					    </select>
					
					</div>
					
					<div class="D-Filtrar">
				      
				      <label>Filtrar</label>
				      
				      <input
				      	type="text" 
				      	class="excrever"
				      	placeholder="Filtrar por nome"
				      	v-model="configs.filter">

				    </div>

				</form>

			</section>

			<Alunos :list="list" 
				@deleteStudant="value => {deleteStudant = value}"
				@remove="value => {remove = value}"
			></Alunos>

		</main>

	</div>

</template>
<script>
import _ from 'lodash'
import Alunos from './Alunos.vue'

export default{
	name: 'Filtrar',
	data(){
		return{
			remove: false,
			deleteStudant: '',
			configs:{
		    	orderBy: 'name',
		    	order: 'desc',
		    	filter: ''
   			},
			alunos:[
				{
					name:'Marco',
					age: '15'
				},
				{
					name:'Gabriel',
					age: '15'
				},
				{
					name:'Romulo',
					age: '20'
				},
				{
					name:'Joao',
					age: '30'
				}
			]
		}
		
	},
	watch:{
		deleteStudant(){
			if(this.remove === true){
				this.alunos.splice(this.deleteStudant,1)
				this.remove = false
				this.deleteStudant = ''
			}
		}
	},
	computed:{
		list() {
      		const filter = this.configs.filter
      		const list = _.orderBy(this.alunos, this.configs.orderBy, 
      			this.configs.order)

      		if (_.isEmpty(filter)){
      			return list
      		}

      		return _.filter(list, aluno => aluno.name.indexOf(filter) >= 0)
		}
 	},
 	components: {
 		Alunos
 	}   
}
</script>

<style scoped>

#html-principal{
background-color: black;
margin: 0;
padding: 0;
}
.main{
background-color: red;
margin: 0;
padding: 0;
}
.sec{
background-color: blue;
margin: 0;
padding: 0;
}
.form{
background-color: green;
margin: 0;
padding: 0;
}
.A-titulos{
background-color: pink;
margin: 0;
padding: 0;
}
.B-usuario{
background-color: yellow;
margin: 0;
padding: 0;
}
.C-cresente{
background-color: #FF7F00;
margin: 0;
padding: 0;
}
.D-Filtrar{
background-color: #8B668B;
margin: 0;
padding: 0;
}
</style>