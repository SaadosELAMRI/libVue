<template>
	<div class="ui-card" >
		<div class="ui-card-header">
			<div class="ui-card-title">Inserer Auteur</div>
		</div>
		<div class="ui-card-body" v-if="ok">
			<div class="ui-alert ui-alert-success">
			  <div class="ui-alert-title">Opération réussie</div>
			  Ajout terminé avec succès
			</div>
		</div>
		<div class="ui-card-body" v-if="busy">
			<div class="ui-spinner ui-spinner-success ui-my-3 "></div>
		</div>
		<div class="ui-card-body" v-if="error">
			<div  class="ui-tip ui-tip-error ui-tip-exclamation ui-my-3">
				<code class="ui-code ui-field"  >{{ error }}</code>
			</div> 
		</div> 
		<div class="ui-card-body" v-if="!ok" >
			<form class="ui-form" @submit.prevent="submitForm" method="POST" novalidate="novalidate" > 
				<fieldset :disabled="busy">
					<div class="ui-field ui-my-3">
						<div class="ui-field-label" >Nom Complet</div>
						<input type="text" class="ui-input ui-input-fluid" placeholder="Nom Complet" v-model="T.nomComplet" required/>
					</div>
					<div class="ui-field ui-my-5">
						<input type="submit" class="ui-btn ui-btn-success ui-float-right" value="Ajouter" />
					</div>
				</fieldset> 
			</form>
		</div>
	</div>
</template>
<script>
	import api_fetch from "../../shared/api_fetch.js"
	export default {
	    data() {
	      return {
	      	T:{nomComplet:null},
	        busy:false,
	        ok:false,
	        error: null,
	      };
	    },
	    methods: {
	      	submitForm: async function (e) {
	      		const [ok,message] = await api_fetch(this,'post',config.URL_AUTEUR,this.T,'ok');
	      		if (ok)
	      			setTimeout(()=>{this.$router.push('/auteur')},1000);
	    	}
	    },
	};
</script>
