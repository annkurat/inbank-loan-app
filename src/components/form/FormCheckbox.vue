<template>
	<div class="row align-items-center">
		<b-form-checkbox v-model="checked">
			{{ text }}
		</b-form-checkbox>
		<b-icon
			v-if="isPopup"
			@click="showModal"
			class="ml-auto"
			icon="exclamation-circle" />
		<b-modal ref="popup-modal" title="PEP" hide-footer>
			<p class="my-4">
				Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
				tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
				veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
				commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
				velit esse cillum dolore eu fugiat nulla pariatur.
			</p>
		</b-modal>
	</div>
</template>
<script>
export default {
	props: {
		text: { type: String, required: true },
		isPopup: { type: Boolean, default: false },
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
	methods: {
		showModal() {
			this.$refs["popup-modal"].show();
		},
	},
};
</script>
