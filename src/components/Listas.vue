<template> 

	<div id="html-principal"> 	
	
		<main class="main">
			
			<section class="sec">
				
				<form  class="form">
					
					<div class="A-titulos">
			
						<h1 class="titulo">Listas de alunos do vnw</h1>
						<h2 class="subtitulo">modulo 2</h2>
					
					</div>
					<hr>
					<div class="B-usuario">
					
						<label>Ordenar por:</label>
					
						<select class="nome-idade" v-model="configs.orderBy">
        				
        					<option value="name" class="nome">Nome</option>				
        					<option value="age" class="idade">Idade</option>
					
					</select>
					
					</div>
					
					<div class="C-cresente">
						
						<label>Orderm:</label>
					    
					    <select class="nome-idade" v-model="configs.order">
					        
					        <option value="asc">Crescente</option>
					        <option value="desc">Decrescente</option> 
					
					    </select>
					
					</div>
					
					<div class="D-Filtrar">
				      
				      <input
				      	type="text" 
				      	class="nome-idade"
				      	placeholder="Filtrar por nome"
				      	v-model="configs.filter">

				      	<button class="nome-idade">Filtrar</button>

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
background-color: #DEE3F5;
margin: 0;
padding: 0;
}
.main{
background-color: #DEE3F5;
margin: 0;
padding: 0;
}
.sec{
background-color: #DEE3F5;
margin: 0;
padding: 0;
}
.form{
background-color: #DEE3F5;
margin: 0;
padding: 0;
}
.A-titulos{
background-color: #DEE3F5;
margin: 0;
padding: 0;
}
.titulo{
	color: #6D90EA;
	margin: 0;
	padding: 0;
}
.subtitulo{
color: #C2C3E0;
margin: 0;
padding: 0;
}
.B-usuario{
background-color: #DEE3F5;
margin: 0;
padding: 0;
display: flex;
justify-content: flex-end;
}
.nome-idade{
	background-color: #FF4D68;
}
.C-cresente{
background-color: #DEE3F5;
margin: 0;
padding: 0;
display: flex;
justify-content: flex-end;
}
.D-Filtrar{
background-color: #DEE3F5;
margin: 0;
padding: 0;
display: flex;
justify-content: flex-start;
}
</style>