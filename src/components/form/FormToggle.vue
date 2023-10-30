<template>
	<div>
		<b-form-checkbox v-model="checked" switch>
			{{ text }}
		</b-form-checkbox>
	</div>
</template>
<script>
export default {
	props: {
		text: { type: String, default: "" },
	},
	computed: {
		checked: {
			get() {
				return this.value;
			},
			set(newValue) {
				this.$emit("input", newValue);
			},
		},
	},
};
</script>
