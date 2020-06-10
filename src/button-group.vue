<template>
	<div class="g-button-group">
		<slot></slot>
	</div>
</template>

<script>
	export default {
		name: "button-group",
		mounted() {
			for (let node of this.$el.children) {
				if (node.nodeName !== "BUTTON") {
					console.warn(`g-button-group 的子元素应该全是button, 传入的是${node.nodeName}`)
				}
			}
		}
	}
</script>

<style scoped lang="scss">
	.g-button-group {
		display: inline-flex;
		vertical-align: middle;
		> .g-button {
			border-radius: 0;
			margin-right: -1px;
			&:first-child {
				border-top-left-radius: var(--border-radius);
				border-bottom-left-radius: var(--border-radius);
			}

			&:last-child {
				border-top-right-radius: var(--border-radius);
				border-bottom-right-radius: var(--border-radius);
			}

			&:hover {
				position: relative;
				z-index: 1;
			}
		}
	}
</style>
