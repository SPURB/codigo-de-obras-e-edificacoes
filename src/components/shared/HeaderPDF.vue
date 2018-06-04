<template>
	<div class="HeaderPDF">
		<a href="http://gestaourbana.prefeitura.sp.gov.br/wp-content/uploads/2018/04/codigo_de_obras_ilustrado.pdf" download="Código de Obras Ilustrado">
			<span>Fazer o download integral do COE</span>
			<i class="small material-icons" title="Fazer o download integral do COE">picture_as_pdf</i>
		</a>
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
	a { color: #333; };
	a:hover {
		color: #EB5757;
	};
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
		flex-grow: 0;
		span {
			display: none;
		};
		i { margin: 0; }
	}
}
</style>