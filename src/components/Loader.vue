<template>
	<div>
		<div class="lds-dual-ring"></div>
	</div>
</template>

<style scoped>
	.lds-dual-ring {
		margin-top: 5rem;
		display: inline-block;
		width: 64px;
		height: 64px;
	}
	.lds-dual-ring:after {
		content: " ";
		display: block;
		width: 46px;
		height: 46px;
		margin: 1px;
		border-radius: 50%;
		border: 5px solid #dfc;
		border-color: #dfc transparent #dfc transparent;
		animation: lds-dual-ring 1.2s linear infinite;
	}
	@keyframes lds-dual-ring {
		0% {
			transform: rotate(0deg);
		}
		100% {
			transform: rotate(360deg);
		}
	}
</style>