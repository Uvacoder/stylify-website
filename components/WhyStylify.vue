<!--
stylify-components
	'why-stylify__block': `
		margin-left:24px margin-bottom:24px background:lighten($blue3,20) padding:12px
		width:100% sm:width:calc(50%_-_24px) lg:width:calc(100%_*_1/3_-_24px) border-radius:$radius2
	`,
	'why-stylify__block-title': 'margin:0 font-size:22px line-height:38px display:flex flex-direction:row align-items:center',
	'why-stylify__block-title-icon': 'font-weight:bold color:$blue1 width:24px height:24px display:inline-block margin-right:8px',
	'why-stylify__list': 'margin-bottom:0 margin-top:4px padding-left:24px color:lighten($blue4,20)'
/stylify-components
-->
<template>
	<div class="display:flex margin-left:-24px flex-wrap:wrap">
		<div class="why-stylify__block">
			<h3 class="why-stylify__block-title">
				<i class="icon icon-heart why-stylify__block-title-icon"></i>
				<span>Don't study selectors</span>
			</h3>
			<ul class="why-stylify__list">
				<li>Use CSS <code class="white-space:nowrap">property:value</code> syntax like <code class="white-space:nowrap">color:blue</code> as a selector.</li>
				<li>Don't waste your time by studying framework shortcuts.</li>
			</ul>
		</div>
		<div class="why-stylify__block">
			<h3 class="why-stylify__block-title">
				<i class="icon icon-layers why-stylify__block-title-icon"></i>
				<span>Copy&paste integration</span>
			</h3>
			<ul class="why-stylify__list">
				<li>Stylify works with any tool: <nuxt-link to="/docs/integrations/nuxtjs" class="color:$blue1">Nuxt.js</nuxt-link>, <nuxt-link to="/docs/integrations/nextjs" class="color:$blue1">Next.js</nuxt-link>, <nuxt-link to="/docs/integrations/webpack" class="color:$blue1">Webpack</nuxt-link>, <nuxt-link to="/docs/integrations/rollupjs" class="color:$blue1">Rollup</nuxt-link>, <nuxt-link to="/docs/integrations/vitejs" class="color:$blue1">Vite.js</nuxt-link>, <nuxt-link to="/docs/integrations/symfony" class="color:$blue1">Symfony</nuxt-link>, <nuxt-link to="/docs/integrations/nette" class="color:$blue1">Nette</nuxt-link>, <nuxt-link to="/docs/integrations/laravel" class="color:$blue1">Laravel</nuxt-link>.</li>
				<li>Generated CSS can be used within SCSS, Less and Stylus projects.</li>
			</ul>
		</div>
		<div class="why-stylify__block">
			<h3 class="why-stylify__block-title">
				<i class="icon icon-settings why-stylify__block-title-icon"></i>
				<span>Simplify your work</span>
			</h3>
			<ul class="why-stylify__list">
				<li>Define reusable <nuxt-link to="/docs/stylify/compiler#components" class="color:$blue1">Components</nuxt-link>, <nuxt-link to="/docs/stylify/compiler#variables" class="color:$blue1">Variables</nuxt-link>, <nuxt-link to="/docs/stylify/compiler#helpers" class="color:$blue1">Helpers</nuxt-link> and style selectors like <code class="white-space:nowrap">article > h1</code> with <nuxt-link to="/docs/stylify/compiler#customselectors" class="color:$blue1">Custom Selectors</nuxt-link>.</li>
				<li>Variables can be injected into the CSS as CSS variables and used outside of generated CSS.</li>
			</ul>
		</div>
		<div class="why-stylify__block">
			<h3 class="why-stylify__block-title">
				<i class="icon icon-layout why-stylify__block-title-icon"></i>
				<span>Style any device</span>
			</h3>
			<ul class="why-stylify__list">
				<li>Combine screens using <nuxt-link to="/docs/stylify/compiler#logical-operands-in-screens" class="color:$blue1">logical operands</nuxt-link> like <code class="white-space:nowrap">sm&&tolg</code>, <code class="white-space:nowrap">xl||landscape</code> and <code class="white-space:nowrap">lg&&dark</code>.</li>
				<li>Dynamic sizes for screens such as <code class="white-space:nowrap">minw640px</code> minimizes the amount of screens.</li>
			</ul>
		</div>
		<div class="why-stylify__block">
			<h3 class="why-stylify__block-title">
				<i class="icon icon-pie-chart why-stylify__block-title-icon"></i>
				<span>Extremely small CSS Chunks</span>
			</h3>
			<ul class="why-stylify__list">
				<li>60-70% smaller CSS - result of our tests</li>
				<li>CSS can be generated for each file, page, layout or component separately.</li>
				<li>Selector is generated only once and reused when possible.</li>
				<li>Selectors can be shrinked in production <code class="white-space:nowrap">.color:blue</code> => <code class="white-space:nowrap">.a</code> </li>
			</ul>
		</div>
		<div class="why-stylify__block">
			<h3 class="why-stylify__block-title">
				<i class="icon icon-archive why-stylify__block-title-icon"></i>
				<span>Works with any tool</span>
			</h3>
			<ul class="why-stylify__list">
				<li>Stylify is standalone library.</li>
				<li>No pre/postprocessor is required.</li>
				<li>Works with any file format and in any environment where javascript is supported.</li>
			</ul>
		</div>
	</div>
</template>
