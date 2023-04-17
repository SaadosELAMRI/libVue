<script setup>
	import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
	<div>
		<div class="ui-tabs ui-tabs-boxed ">
			<RouterLink to="/auteur" class="ui-tabs-item ui-tabs-item ui-link">Liste d'Auteurs</RouterLink>
			<RouterLink to="/auteur/inserer" class="ui-tabs-item ui-tabs-item ui-link" >Inserer auteur</RouterLink>
		</div>
		<RouterView />
	</div>
</template>



