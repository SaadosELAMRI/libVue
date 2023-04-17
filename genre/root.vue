<script setup>
	import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
	<div>
		<div class="ui-tabs ui-tabs-boxed ">
			<RouterLink to="/genre" class="ui-tabs-item ui-tabs-item ui-link">Liste du genres</RouterLink>
			<RouterLink to="/genre/inserer" class="ui-tabs-item ui-tabs-item ui-link" >Inserer genre</RouterLink>
		</div>
		<RouterView />
	</div>
</template>



