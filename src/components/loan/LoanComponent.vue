<template>
	<div
		v-if="!isEdit"
		class="p-3 col-lg-9 col-md-12 bg-primary rounded-pill text-white">
		<div class="d-flex align-items-center">
			<b-button
				@click="isEdit = true"
				variant="primary"
				class="icon-btn rounded-circle d-flex justify-content-center align-items-center">
				<b-icon scale="0.7" icon="chevron-left" variant="white" />
			</b-button>

			<p class="row mx-auto align-items-center m-0 justify-content-center">
				Your loan application
				<small class="ml-2 mt-0 text-white font-weight-light"
					>{{ amount }}€/{{ duration }}months</small
				>
			</p>
		</div>
	</div>
	<div
		v-else
		class="d-flex loan__container--edit col-lg-9 col-md-12 align-items-center bg-primary text-white p-3">
		<div
			class="gap-y-20 row mx-auto align-items-center m-0 justify-content-center">
			<div
				class="col-12 col-md-4 d-flex align-items-center justify-content-center">
				<small class="font-weight-light">Amount</small>
				<b-form-input class="transparent-input col-md-6" v-model="amount" />€
			</div>
			<div
				class="col-12 col-md-4 d-flex align-items-center justify-content-center">
				<small class="font-weight-light">Duration</small>
				<b-form-input
					class="transparent-input col-md-3"
					v-model="duration" />months
			</div>

			<div class="loan__monthly-payment rounded-pill px-3 py-1">
				<small class="font-weight-light"
					>Monthly Payment<span class="ml-2 font-weight-normal"
						>95,27€
					</span></small
				>
			</div>
		</div>
		<b-button
			@click="isEdit = false"
			variant="secondary"
			class="icon-btn rounded-circle d-flex justify-content-center align-items-center">
			<b-icon scale="0.7" icon="chevron-right" variant="primary" />
		</b-button>
	</div>
</template>
<script>
export default {
	data() {
		return {
			isEdit: false,
			amount: 2700,
			duration: 36,
		};
	},
};
</script>
<style lang="scss" scoped>
.icon-btn {
	border: 0;
	width: 2rem;
	height: 2rem;
	transition: all 0.5s ease;

	&:hover {
		scale: 1.05;
		box-shadow: 0 1px 25px 4px #5948ad;
	}
}
.gap-y-20 {
	row-gap: 20px;
}
.loan {
	&__container {
		&--edit {
			border-radius: 30px;
		}
	}
	&__monthly-payment {
		background-color: #3a156c;
	}
}
.transparent-input {
	background: transparent;
	color: white;
	border: none;
	border-radius: 0;
	border-bottom: 1px solid #ccc;
	&:focus {
		background: transparent;
		box-shadow: none;
		color: white;
		border-bottom: 2px solid;
	}
}
</style>
