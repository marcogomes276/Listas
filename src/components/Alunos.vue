<template>
	<section id="A">
		<ul class="B">	
			<li v-for="(aluno,index) in list" class="C">
				{{ aluno.name }}
				{{ aluno.age }} anos
				<button @click="deleteStudant(index)" class="D">x</button>
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
	},
	methods:{
		deleteStudant(value){
			this.$emit('deleteStudant',value)
			this.$emit('remove',true)
		}
	}
}

</script>

<style>
body{
	margin-top: 220px;
	padding: 0; 
}
#app{
	margin: 60px;
	padding: 0;
}
.A{
	margin: 0;
	padding: 0;
}
.B{
	margin: 0;
	padding: 0;
}
.C{
	margin: 0;
	padding: 0;
}
.D{
	margin: 0;
	padding: 0;
}
</style>