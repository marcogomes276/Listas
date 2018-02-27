<template>
	<div id="appFilter">
		<main>
			<section class="container">
				<form  class="form">
					<div>
						<label>Ordenar por:</label>
						<select class="form-control" v-model="configs.orderBy">
        					<option value="name">Nome</option>				
        					<option value="age">Idade</option>
					</select>
					</div>
					<div>
						<label>Orderm:</label>
					    <select class="form-control" v-model="configs.order">
					        <option value="asc">Crescente</option>
					        <option value="desc">Decrescente</option>					 
					    </select>
					</div>
					<div class="form-group">
				      <label>Filtrar</label>
				      <input
				      	type="text" 
				      	class="form-control"
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

</style>