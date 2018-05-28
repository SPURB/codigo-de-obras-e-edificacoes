<template>
	<div class="HeaderPDF">
		{{ dlmsg }} <i class="small material-icons">file_download</i>
	</div>
</template>

<script>
export default {
	name: 'HeaderPDF',
	data() {
		return {
			dlmsg: 'Baixar PDF do COE'
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
	text-transform: uppercase;
	i { float: right; margin-left: 12px; }
}
.HeaderPDF:hover {
	i {	color: #EB5757; };
	cursor: pointer;
}
</style>