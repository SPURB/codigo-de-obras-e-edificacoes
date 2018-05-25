<template>
	<div class="HeaderMenu">
		<div class="menu" @click="showMenu = !showMenu">
			{{ tituloMenu }}
			<i class="small material-icons" v-if="!showMenu">arrow_drop_down</i>
			<i class="small material-icons" v-else>arrow_drop_up</i>
		</div>

		<div class="menu-exp" v-if="showMenu">
			<ul>
				<template v-for="navitem in navItems" >
					<li @click="showMenu = !showMenu">
						<router-link :to='navitem.path' active-class="menuLi"><div>{{ navitem.name }}</div></router-link>
					</li>
				</template>
			</ul>
		</div>
	</div>
</template>

<script>
export default {
	name: 'HeaderMenu',
	data() {
		return {
			tituloMenu: "Seções",
			showMenu: false,
		}
	}, 
	props:['navItems']
}
</script>

<style lang="scss" scoped>
.HeaderMenu {
	div.menu {
		max-height: 24px;
		padding: 12px;
		line-height: 24px;
		font-size: 15px;
		text-transform: uppercase;
		font-weight: 500;
		color: #EB5757;
		cursor: pointer;
		min-width: 150px;
		box-sizing: border-box;
		i { float: right; margin-left: 12px; }
	}

	div.menu-exp {
		position: absolute;
		border: 1px solid #BDBDBD;
		border-radius: 0 0 2px 2px;
		box-shadow: 0 2px 2px rgba(0,0,0,0.12);
		background-color: #FFF;
		right: 0px;
		top: 48px;
		width: 151px;
		box-sizing: border-box;
		ul li {
				div {
					line-height: 32px;
					padding: 0 12px;
				}
				div:hover {
					background-color: #EEE;
				}
		};
	}

}
</style>