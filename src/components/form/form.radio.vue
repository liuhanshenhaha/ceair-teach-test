<template>
	<div class="form-radio">
		<label class="form-label" v-html="idx+1+'.'+data.label"></label>
		<ul>
			<li v-for="(item, index) in data.list" :key="index">
				<input type="radio" :id="data.name + index" :name="data.name" :value="item.value" :checked="item == data.value" @change="updateValue($event.target.value)"/>
				<label :for="data.name + index">{{item.text}}</label>
			</li>
		</ul>
	</div>
</template>

<script>
	export default {
	  name: 'radio-box',
	  props: {
	    data: Object,
	    idx: Number
	  },
	  methods: {
	  	updateValue: function(value){
	  		this.$emit('updateValue',this.data.name,value)
	  	}
	  }
	}
</script>