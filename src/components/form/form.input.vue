<template>
	<div class="form-input">
		<label class="form-label">{{data.label}}</label>
		<div>
			<input type="text" :id="data.name" :name="data.name" :placeholder="data.label" :value="data.value" @change="updateValue($event.target.value)"/>
		</div>
	</div>
</template>

<script>
	export default {
	  name: 'radio-box',
	  props: {
	    data: Object
	  },
	  methods: {
	  	updateValue: function(value){
	  		this.$emit('updateValue',this.data.name,value)
	  	}
	  }
	}
</script>