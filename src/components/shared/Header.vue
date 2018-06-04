<template>
	<div class="Header" :class="{ scrollOn: scrolling }">
		<div class="nav">
			<div class="tituloSecao">{{ sectionName }}</div>
			<div class="navDiv">
				<HeaderPDF :navItems="navitems"></HeaderPDF>
				<HeaderMenu :navItems="navitems"></HeaderMenu>
			</div>
		</div>
		<div class="degradeBranco"></div>
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

div.tituloSecao {
	font-size: 30px;
	font-weight: 700;
	align-self: center;
	line-height: 48px;
}

div.navDiv {
	display: flex;
	flex-direction: row;
}

.degradeBranco {
	background: linear-gradient(#FFFFFF, rgba(255,255,255,0));
	height: 60px;
	margin-bottom: -40px;
}

@media (min-width: 960px){
	#app > .Header {
		margin-top: 69px;
	}
	#app > .Header.scrollOn{
		position: fixed;
		top: 35px;
		z-index: 100
	}
}

@media (max-width: 560px) {
	#app > .Header, #app > .Header.scrollOn {
		margin-top: 89px;
	}
}

@media (min-width: 561px) {
	#app > .Header, #app > .Header.scrollOn {
		margin-top: 69px;
	}
}

@media (max-width: 959px) {
	div.nav {
		flex-direction: column-reverse !important;
	}
	div.tituloSecao {
		width: 100%;
	}
	div.navDiv {
		flex-wrap: wrap-reverse;
		justify-content: space-between;
		flex-direction: row-reverse;
		width: 100%;
		border-bottom:1px solid #EEEEEE;
		flex-wrap: nowrap;
	}
}
</style>