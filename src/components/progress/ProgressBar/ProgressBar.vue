<template>
	<div class="progress-bar">
		<transition name="progress" appear>
			<span
				class="progress-line"
				:style="{transitionDuration: animationDuration + 'ms' }"
			/>
		</transition>
	</div>
</template>

<script>
import percentage from '@/utils/percentage';

export default {
	props: {
		animationDuration: {
			type: Number,
			default: 0
		}
	},

	computed: {
		progressBarColor () {
			let progressBarColor;
			const BAR_FULL_WIDTH = 100;

			if (this.progressBarWidth === null) {
				progressBarColor = 'var(--primary-yellow)';
			}
			else if (this.progressBarWidth < BAR_FULL_WIDTH) {
				progressBarColor = 'currentColor';
			}
			else {
				progressBarColor = '#d1f749';
			}
			return progressBarColor;
		},

		progressBarWidth () {
			return percentage(this.value, this.length);
		}
	}
};
</script>

<style scoped>
.progress-bar {
	height: var(--progress-bar-height, 0.188em);
	background-color: var(--progress-bar-background-color, #404040);
	color: #fff;
	width: 100%;
	border-radius: 1em;
	position: relative;
	overflow: hidden;
}

.progress-enter-active, .progress-leave-active {
  width: 100%;
}
.progress-enter, .progress-leave-to /* .fade-leave-active до версии 2.1.8 */ {
  width: 0;
}

.progress-bar .progress-line {
	height: inherit;
	border-radius: inherit;
	display: block;
	background-color: #fff;
	transition-timing-function: linear;
}
</style>