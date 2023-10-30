<template>
	<div id="app" class="text-center d-flex flex-column align-items-center">
		<AppHeader />
		<div class="container">
			<LoanView />
		</div>
	</div>
</template>

<script>
import AppHeader from "@/components/common/AppHeader.vue";
import LoanView from "@/views/LoanView.vue";

export default {
	components: {
		AppHeader,
		LoanView,
	},
};
</script>
