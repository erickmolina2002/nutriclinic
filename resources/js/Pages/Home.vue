<template>
    <div class="app">
        <MenuBar/>
        <h1>Hello world</h1>
    </div>
</template>
<script>
import { Link } from '@inertiajs/vue3';
import MenuBar from './components/MenuBar.vue';

export default {
    components: { Link, MenuBar }
}
</script>
<style lang="scss">
:root {
	--primary: #306fe5;
	--primary-alt: #226bc5;
	--grey: #64748b;
	--dark: #1e293b;
	--dark-alt: #334155;
	--light: #f1f5f9;
	--sidebar-width: 300px;
}

* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
	font-family: 'Fira sans', sans-serif;
}

body {
	background: var(--light);
}

button {
	cursor: pointer;
	appearance: none;
	border: none;
	outline: none;
	background: none;
}

.app {
	display: flex;

	main {
		flex: 1 1 0;
		padding: 2rem;

		@media (max-width: 1024px) {
			padding-left: 6rem;
		}
	}
}
</style>