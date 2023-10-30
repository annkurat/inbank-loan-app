<template>
	<div
		class="col-lg-9 col-md-12 bg-secondary customer-component-block overflow-hidden">
		<div class="py-2 d-flex justify-content-between align-items-center">
			<p v-if="!isEdit" class="mx-auto">Anna Maria Tamm Rodriguez Espinosa</p>
			<div
				v-else
				class="row w-100 justify-content-around col-12 align-items-center">
				<small class="col-12 col-md-4">Change your contact Info </small>
				<div
					class="col-12 col-md-4 d-flex align-items-center justify-content-center">
					<b-icon icon="telephone" scale="0.75" class="mr-1" />
					+372<b-form-input
						class="ml-1 transparent-input"
						:state="phoneNumber ? true : false"
						v-model="phoneNumber" />
				</div>
				<div
					class="col-12 col-md-4 d-flex align-items-center justify-content-center">
					<b-icon icon="envelope" scale="0.75" class="mr-1" />
					<b-form-input
						class="transparent-input"
						:state="email ? true : false"
						v-model="email" />
				</div>
			</div>
			<b-button
				@click="isEdit = !isEdit"
				:disabled="!phoneNumber || !email"
				variant="outline-primary"
				class="icon-btn rounded-circle d-flex justify-content-center align-items-center">
				<b-icon scale="0.7" icon="pen" variant="outline-primary" />
			</b-button>
		</div>

		<div v-if="!isEdit" class="row bg-white p-2">
			<div class="col-md-4 col-12">
				<b-icon icon="person" scale="0.75" class="mr-1" /><span
					>38912052254</span
				>
			</div>
			<div class="col-md-4 col-12">
				<b-icon icon="telephone" scale="0.75" class="mr-1" /><span
					>+372 {{ phoneNumber }}</span
				>
			</div>
			<div class="col-md-4 col-12">
				<b-icon icon="envelope" scale="0.75" class="mr-1" />
				<span>{{ email }}</span>
			</div>
		</div>
	</div>
</template>
<script>
export default {
	data() {
		return {
			isEdit: false,
			phoneNumber: "5289 6572",
			email: "anna.tamm@gmail.com",
		};
	},
};
</script>
<style lang="scss" scoped>
@import "@/assets/styles/main";

.icon-btn {
	border: 0;
	width: 2rem;
	height: 2rem;
	transition: all 0.5s ease;
	background-color: white;

	&:hover {
		scale: 1.05;
		box-shadow: 0 1px 25px 4px #5948ad;
	}
}
.customer-component-block {
	border-radius: 30px;
	border: 5px solid #f3eefb;
}
.transparent-input {
	background: transparent;
	border: none;
	border-radius: 0;
	border-bottom: 1px solid #ccc;
	&:focus {
		background: transparent;
		box-shadow: none;
		border-bottom: 2px solid $color-primary;
	}
}
</style>
