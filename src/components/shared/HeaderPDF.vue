<template>
	<div class="HeaderPDF">
		<span>Fazer o download integral do COE</span>
		<i class="small material-icons" title="Fazer o download integral do COE">picture_as_pdf</i>
	</div>
</template>

<script>
export default {
	name: 'HeaderPDF',
	data() {
		return {
		}
	},
	props:['navItems']
}
</script>

<style lang="scss" scoped>
.HeaderPDF {
	max-height: 24px;
	padding: 12px;
	line-height: 24px;
	font-size: 15px;
	font-weight: 500;
	color: #333;
	border-right: 1px solid #EEEEEE;
	i { float: right; margin-left: 12px; }
}
.HeaderPDF:hover {
	i {	color: #EB5757; };
	cursor: pointer;
}
@media (max-width: 959px) {
	.HeaderPDF {
		border-right: 0;
		border-left:1px solid #EEEEEE;
		span {
			display: none;
		};
		i { margin: 0; }
	}
}
</style>