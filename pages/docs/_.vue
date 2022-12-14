<template>
	<DocsContainer>
		<DocsSidebar :items="navigationItems" :urlPath="urlPath" ref="sidebar" />
		<DocsContent>
			<DocsArticle :page="pageContent ?? undefined" />
			<DocsFooter :page="pageContent ?? undefined" :nextPage="nextPage ?? undefined" :previousPage="previousPage ?? undefined" />
		</DocsContent>
	</DocsContainer>
</template>

<script>
import { DocsRepository } from '~/services/model/DocsRepository';

export default {
 	asyncData: async ({ $content, params, route, redirect }) => {
		if (route.path.replace(/\/+$/, '') === '/docs') {
			redirect('/docs/get-started');
			return;
		}

		const getNavigationSectionItems = async (section, config) => {
			const docsRepository = new DocsRepository($content);
			return docsRepository.findBySection({
				section: section,
				only: ['navigationTitle', 'slug', 'dir', 'section', 'navigationIconPath', 'path']
			})
		};

		let urlPath = params.pathMatch || params.slug || 'get-started';
		let urlPathToArray = urlPath.split('/');

		const navigationItems = {};
		const navigationSectionsConfig = {
			'get-started': {
				sort: ['order', 'asc']
			},
			'integrations': {},
			'stylify': {},
			'bundler': {},
			'unplugin': {},
			'astro': {},
			'nuxt': {},
			'nuxt-module': {},
		};
		for (const section of Object.keys(navigationSectionsConfig)) {
			navigationItems[section] = await getNavigationSectionItems(section, navigationSectionsConfig[section]);
		}
		const whereConditionKey = urlPathToArray.length >= 2 ? 'path' : 'slug';
		let pageContent = await $content('docs', { deep: true})
			.where({
				[whereConditionKey]: urlPathToArray.length >= 2 ? `/docs/${urlPath}` : urlPath
			})
			.fetch();

		pageContent = pageContent[0];

		let pageIndexInNavigation = pageContent[whereConditionKey] in navigationItems ? 0 : null;

		if (pageIndexInNavigation === null) {
			navigationItems[pageContent.section].find((navigationItem, key) => {
				if (navigationItem[whereConditionKey] === pageContent[whereConditionKey]) {
					pageIndexInNavigation = key;
					return true
				}
				return false
			});
		}

		return {
			urlPath: urlPath,
			pageContent: pageContent || null,
			previousPage: pageIndexInNavigation > 0
				? navigationItems[pageContent.section][(pageIndexInNavigation - 1)]
				: null,
			nextPage: navigationItems[pageContent.section][(pageIndexInNavigation + 1)] || null,
			navigationItems: navigationItems
		}
	},
	head() {
		if (!this.pageContent) {
			return;
		}

		const pageTitle = this.pageContent.title + ' | Stylify';

		return {
			title: pageTitle,
			meta: [
				{ hid: 'description', name: 'description', content: this.pageContent.description },
				// Open Graph
				{ hid: 'og:title', property: 'og:title', content: pageTitle },
				{ hid: 'og:description', property: 'og:description', content: this.pageContent.description },
				// Twitter Card
				{ hid: 'twitter:title', name: 'twitter:title', content: pageTitle },
				{ hid: 'twitter:description', name: 'twitter:description', content: this.pageContent.description }
			]
		}
	}
}
</script>
