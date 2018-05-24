<template>
	<div class="Header" :class="{ scrollOn: scrolling }">
		<h3>{{ sectionName }}</h3>
		<HeaderPDF :navItems="navitems"></HeaderPDF>
		<HeaderMenu :navItems="navitems"></HeaderMenu>
	</div>
</template>

<script>
import HeaderMenu from '@/components/shared/HeaderMenu'
import HeaderPDF from '@/components/shared/HeaderPDF'

export default {
	name: 'Header',
	data () {
		return {
			showMenu: false,
			navitems: [],
			scrolling: false
		}
	},
	computed: {
		sectionName() { return this.$route.name }
	},
	created: function () {
		this.createNavitems();
		window.addEventListener('scroll', this.handleScroll);
	},
	destroyed: function () {
		window.removeEventListener('scroll', this.handleScroll);
	},
	methods:{
		handleScroll: function (event) {
			document.documentElement.scrollTop > 1 ? this.scrolling = true : this.scrolling = false
		},
		createNavitems(){
			const app = this;
			const routes = this.$router.options.routes;
			routes.filter(function(index) {
				if('name' in index){
					app.navitems.push(index)
				}
			})
		}
	},
	components: { 
		HeaderPDF, 
		HeaderMenu 
	}
}
</script>

<style lang="scss">
@import '../../assets/main.scss';

@media (min-width: 960px){
		#app > .Header {
			margin-top: -3.14em
		}
		#app > .Header.scrollOn{
		position: fixed;
		margin-top: -5.6em;
		background-color: white;
		z-index: 100
	}
}
</style>