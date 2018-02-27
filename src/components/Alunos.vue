<template>
	<section>
		<ul class="lista">	
			<li v-for="aluno in list" class="lista">
			{{ aluno.name }}
			{{ aluno.age }} anos
			</li>
		</ul>
	</section>
</template>

<script>
export default{
	name: 'Alunos',
	props:{
		list:{
			type: Array,
			required: true
		}
	},
	data(){
		return{

		}
	}
}

</script>

<style>
	
</style>