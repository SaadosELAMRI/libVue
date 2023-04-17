<template>
	<div class="ui-card" >
		<div class="ui-card-header">
			<div class="ui-card-title">Liste du genres</div>
		</div>
		<div class="ui-card-body" v-if="ok">
			<div class="ui-alert ui-alert-success">
			  <div class="ui-alert-title">Opération réussie</div>
			  La suppression a été effectuée avec succès
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
		
		<div class="ui-card-body ui-card-body-table" v-if="TT">
			<div class="ui-table" >
			    <div class="ui-table-header">
			        <div class="ui-table-row">
			            <div class="ui-table-cell">#</div>
			            <div class="ui-table-cell">Genre</div>
			            <div class="ui-table-cell">Date d'ajout</div>
			            <div class="ui-table-cell">Action</div>
			        </div>
			    </div>
			    <div class="ui-table-body" >
			        <div class="ui-table-row " v-for="T in TT">
			        	<div class="ui-table-cell">{{T.id}}</div>
			            <div class="ui-table-cell">{{T.genre}}</div>
			            <div class="ui-table-cell">{{T.dateAjout}}</div>
			            <div class="ui-table-cell">
							<div 
			            	@click="supprimer(T)"
			            	class="ui-btn ui-btn-small ui-btn-error ui-m-1"><i class="fas fa-trash"></i></div>
			            </div>
			        </div>
			    </div>
			</div>
		</div>
	</div>
</template>
<script>
	import api_fetch from "../../shared/api_fetch.js"
	export default {
	    data() {
	      return {
	      	TT:null,
	        busy:false,
	        ok:false,
	        error:null,
	      };
	    },
	    methods: {
			async supprimer(T){
	      		const [ok,message] = await api_fetch(this,'delete',config.URL_GENRE+'/'+T.id,null,'ok');
	      		if (ok)
	      			setTimeout(()=>{this.$router.go(this.$router.currentRoute);},1000);
			},
	    },
	    async mounted() {
	    	const [ok,message] = await api_fetch(this,'get',config.URL_GENRE);
	      	if (ok)
	      		this.TT=message;
	    },
       

	};
</script>
