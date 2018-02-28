<template>

	<div id="html-principal">
	
		<main class="main">
			
			<section class="sec">
				
				<form  class="form">
					
					<div class="A=titulos">
			
						<h1 class="titulo">Listas de alunos do vnw</h1>
						<h2 class="subtitulo">modulo 2</h2>
					
					</div>
					
					<div class="B=usuario">
					
						<label>Ordenar por:</label>
					
						<select class="form-control" v-model="configs.orderBy">
        				
        					<option value="name">Nome</option>				
        					<option value="age">Idade</option>
					
					</select>
					
					</div>
					
					<div class="C=cresente">
						
						<label>Orderm:</label>
					    
					    <select class="form-control" v-model="configs.order">
					        
					        <option value="asc">Crescente</option>
					        <option value="desc">Decrescente</option> 
					
					    </select>
					
					</div>
					
					<div class="Filtrar">
				      
				      <label>Filtrar</label>
				      
				      <input
				      	type="text" 
				      	class="excrever"
				      	placeholder="Filtrar por nome"
				      	v-model="configs.filter">

				    </div>

				</form>

			</section>

			<Alunos :list="list"></Alunos>

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
	background: white;
	color: #6D90EA;
	height: 80vh;
	margin:0;
	padding: 0;
}
.sec{
	margin: 0;
	padding: 0;
	background-color: white;
}
.main{
	margin: 0;
	padding: 0;
	background-color: white;
}
.A{
	margin: 0;
	padding: 0;
}
.titulo{
	margin: 0;
	padding: 0;
	color: #6D90EA;	
}
.subtitulo{
	margin: 0;
	padding: 0;
	color:  #DEE3F5;
}
</style>