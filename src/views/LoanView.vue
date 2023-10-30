<template>
	<div class="py-4 d-flex flex-column align-items-center">
		<LoanComponent />
		<CustomerComponent class="mt-4" />

		<p class="col-lg-8 mt-4 text-left">Personal information</p>
		<!-- FIELDS FOR PERSONAL INFO -->
		<div class="row w-100 justify-content-center mb-4 mt-3">
			<div class="col-xl-4 col-lg-4 col-md-6 px-md-2 px-0">
				<div class="mb-3">
					<input type="text" class="form-control" placeholder="Country" />
				</div>
				<div class="mb-3">
					<FormSelect v-if="!isAddManuallyAddress" placeholder="City" />
					<input v-else type="text" class="form-control" placeholder="City" />
				</div>
				<div class="mb-3">
					<input type="text" class="form-control" placeholder="Street" />
				</div>
			</div>
			<div class="col-xl-4 col-lg-5 col-md-6 px-md-2 px-0">
				<div class="mb-3">
					<FormSelect v-if="!isAddManuallyAddress" placeholder="Country" />
					<input
						v-else
						type="text"
						class="form-control"
						placeholder="Country" />
				</div>
				<div class="mb-3">
					<FormSelect
						v-if="!isAddManuallyAddress"
						placeholder="Village/Township" />
					<input
						v-else
						type="text"
						class="form-control"
						placeholder="Village/Township" />
				</div>

				<div class="form-row">
					<div class="form-group col-4">
						<input type="text" class="form-control" placeholder="House" />
					</div>
					<div class="form-group col-4">
						<input type="text" class="form-control" placeholder="Apartment" />
					</div>
					<div class="form-group col-4">
						<input type="text" class="form-control" placeholder="Postal Code" />
					</div>
				</div>
			</div>
		</div>

		<div class="hrdivider col-8">
			<hr />
			<span class="col-2 mx-auto font-italic text-black-50">Or</span>
		</div>
		<FormToggle
			v-model="isAddManuallyAddress"
			class="my-2"
			text="Add address manually" />
		<div class="hrdivider col-8 mb-4">
			<hr />
		</div>

		<!-- FIELDS IF CUSTOMER OR FAMILY MEMBER IS PEP -->
		<div class="col-xl-4 col-lg-5 col-md-6 my-2">
			<FormCheckbox
				v-model="isFamilyPEP"
				is-popup
				text="Neither I nor my family member is PEP" />
		</div>
		<div v-if="!isFamilyPEP" class="row w-100 justify-content-center my-4">
			<div class="col-lg-4 col-md-6 px-md-2 px-0">
				<div class="mb-3">
					<FormSelect placeholder="Relationship to the PEP" />
				</div>
				<div class="mb-3">
					<FormSelect placeholder="PEP position" />
				</div>
			</div>
			<div class="col-lg-4 col-md-6 px-md-2 px-0">
				<div class="mb-3">
					<FormSelect placeholder="PEP region" />
				</div>
				<div class="mb-3">
					<FormSelect placeholder="Duration as PEP or related to a PEP" />
				</div>
			</div>
		</div>

		<!-- FIELDS IF CUSTOMER NOT ULTIMATE BENEFICIARY -->
		<div class="col-xl-4 col-lg-5 col-md-6 my-2">
			<FormCheckbox
				v-model="isUltimateBeneficiary"
				is-popup
				text="I’m the ultimate beneficiary" />
		</div>
		<div
			v-if="!isUltimateBeneficiary"
			class="row w-100 justify-content-center my-4">
			<div class="col-lg-4 col-md-6 px-md-2 px-0">
				<div class="mb-3">
					<input type="text" class="form-control" placeholder="First name" />
				</div>
				<div class="mb-3">
					<input
						type="text"
						class="form-control"
						placeholder="Personal ID code" />
				</div>
				<div class="mb-3">
					<input type="text" class="form-control" placeholder="Birth place" />
				</div>
			</div>
			<div class="col-lg-4 col-md-6 px-md-2 px-0">
				<div class="mb-3">
					<input type="text" class="form-control" placeholder="Last name" />
				</div>
				<div class="mb-3">
					<FormSelect placeholder="Residency" />
				</div>
				<div class="mb-3">
					<input type="text" class="form-control" placeholder="Birth place" />
				</div>
			</div>
		</div>

		<!-- FIELDS IF CUSTOMER IS PEP OWNER -->
		<div class="col-xl-4 col-lg-5 col-md-6 my-2">
			<FormCheckbox
				v-model="isBeneficialOwnerPEP"
				text="The beneficial owner is not a PEP" />
		</div>
		<div
			v-if="!isBeneficialOwnerPEP"
			class="row w-100 justify-content-center my-4">
			<div class="col-lg-4 col-md-6 px-md-2 px-0">
				<div class="mb-3">
					<FormSelect placeholder="Relationship to the PEP" />
				</div>
				<div class="mb-3">
					<FormSelect placeholder="PEP position" />
				</div>
			</div>
			<div class="col-lg-4 col-md-6 px-md-2 px-0">
				<div class="mb-3">
					<FormSelect placeholder="PEP region" />
				</div>
				<div class="mb-3">
					<FormSelect placeholder="Duration as PEP or related to a PEP" />
				</div>
			</div>
		</div>

		<b-button class="col-lg-3 col-md-8 col-sm-12 mt-2" variant="primary"
			>Continue</b-button
		>
	</div>
</template>
<script>
import FormCheckbox from "@/components/form/FormCheckbox.vue";
import FormToggle from "@/components/form/FormToggle.vue";
import LoanComponent from "@/components/loan/LoanComponent.vue";
import FormSelect from "@/components/form/FormSelect.vue";
import CustomerComponent from "@/components/loan/CustomerComponent.vue";

export default {
	data() {
		return {
			isFamilyPEP: false,
			isUltimateBeneficiary: false,
			isBeneficialOwnerPEP: false,
			isAddManuallyAddress: false,
		};
	},
	components: {
		FormCheckbox,
		FormToggle,
		LoanComponent,
		FormSelect,
		CustomerComponent,
	},
};
</script>
<style scoped>
.hrdivider {
	position: relative;
	width: 100%;
}

.hrdivider hr {
	border-top: 1px solid rgba(0, 0, 0, 0.05);
}

.hrdivider span {
	position: absolute;
	top: 0;
	bottom: 0;
	left: 0;
	right: 0;
	padding: 0 20px;
	background-color: white;
}
</style>
