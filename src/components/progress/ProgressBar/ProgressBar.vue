<template>
	<div class="progress-bar" :class="{stopped: !start}">
		<transition name="progress" appear>
			<span
				:key="start"
				class="progress-line" 
				:style="{
					transitionDuration: animationDuration + 'ms',
				}"
			/>
		</transition>
	</div>
</template>

<script>
export default {
	name:"ProgressBar",
	props: {
		animationDuration: {
			type: Number,
			default: 0
		},
        start: {
			type: Boolean,
			default: true
		},
	}
}
</script>

<style scoped>
.progress-bar {
	height: var(--progress-bar-height, 0.188em);
	background-color: var(--progress-bar-background-color, #eee);
	color: #fff;
	width: 100%;
	border-radius: 1em;
	position: relative;
	overflow: hidden;
}

.progress-bar .progress-line {
	height: inherit;
	border-radius: inherit;
	display: block;
	transition-timing-function: linear;
}

.progress-bar.stopped .progress-line {
	width: 0;
	transition: none;
}

.progress-enter-active, .progress-leave-active {
  width: 100%;
  background: #fff;
}
.progress-enter, .progress-leave-to {
  width: 0;
}

</style>