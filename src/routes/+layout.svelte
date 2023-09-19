<script>
	import '@spectrum-web-components/theme/scale-medium.js';
	import '@spectrum-web-components/theme/sp-theme.js';
	import '@spectrum-web-components/theme/theme-lightest.js';
	import '@spectrum-web-components/bundle';
	import '@spectrum-web-components/bundle/elements.js';
</script>

<sp-theme theme="spectrum" color="lightest" scale="medium">
	<div class="layout-grid">
		<div class="nav">
			<sp-top-nav>
				<sp-top-nav-item href="/">Scaffold Site</sp-top-nav-item>
				<sp-top-nav-item href="/about" style="margin-inline-start: auto;"> About </sp-top-nav-item>
				<sp-top-nav-item href="/info">Info</sp-top-nav-item>
				<sp-action-menu
					label="Account"
					placement="bottom-end"
					style="margin-inline-start: auto;"
					quiet
				>
					<sp-menu-item>Account Settings</sp-menu-item>
					<sp-menu-item>My Profile</sp-menu-item>
					<sp-menu-divider />
					<sp-menu-item>Share</sp-menu-item>
					<sp-menu-divider />
					<sp-menu-item>Help</sp-menu-item>
					<sp-menu-item>Sign Out</sp-menu-item>
				</sp-action-menu>
			</sp-top-nav>
		</div>
		<div class="sidebar">
			<sp-sidenav defaultValue="Docs">
				<sp-sidenav-item value="Docs" href="/components/SideNav" label="Docs" selected />
				<sp-sidenav-item value="Guides" href="/guides/getting_started" label="Guides" />
				<sp-sidenav-item value="Community" href="/community" label="Community" />
				<sp-sidenav-item value="Storybook" href="/storybook" target="_blank" label="Storybook" />
				<sp-sidenav-item
					value="Releases"
					href="http://git.corp.adobe.com/React/react-spectrum/releases"
					target="_blank"
					label="Releases"
					disabled
				/>
				<sp-sidenav-item
					value="GitHub"
					href="http://git.corp.adobe.com/React/react-spectrum"
					target="_blank"
					label="Github"
				/>
			</sp-sidenav>
		</div>

		<div class="main">
			<slot />
		</div>
	</div>
</sp-theme>

<style>
	:global(body) {
		width: 100vw;
		height: 100vh;
		margin: 0px;
		padding: 0px;
	}
	.nav {
		gird-area: nav;
	}
	.main {
		grid-area: main;
	}
	.sidebar {
		grid-area: sidebar;
	}
	.layout-grid {
		display: grid;
		grid-template-rows: 50px 1fr;
		grid-template-columns: 200px 1fr;
		grid-template-areas:
			'sidebar nav'
			'sidebar main';
	}
</style>
