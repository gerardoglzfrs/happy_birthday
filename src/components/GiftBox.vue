<template>
    <div class="present">
        <div class="name">
            <v-row class="justify-center" >
                <v-col cols="6" sm="6" md="6" lg="6">
                    <v-img max-height="600" max-width="600" src="@/assets/playera.png" alt="Bolillo de soriana"></v-img>
                </v-col>
				<v-col cols="6" sm="6" md="6" lg="6">
                    <v-img max-height="600" max-width="600" src="@/assets/bolillos_de_soriana.png" alt="Bolillo de soriana"></v-img>
                </v-col>
            </v-row>
        </div>
        <div class="rotate-container">
        <div class="bottom"></div>
        <div class="front"></div>
        <div class="left"></div>
        <div class="back"></div>
        <div class="right"></div>
        <div class="lid">
            <div class="lid-top"></div>
            <div class="lid-front"></div>
            <div class="lid-left"></div>
            <div class="lid-back"></div>
            <div class="lid-right"></div>
        </div>
	</div>
</div>
</template>

<script>

import "./giftbox.scss"

export default {
    name: "GiftBox",
    
    mounted() {
        const present = document.querySelector('.present')
    present.onclick = () => present.classList.toggle('open')



;(function () {
	'use strict'

	const canvas = document.querySelector('canvas')
	const ctx = canvas.getContext('2d')

	let width, height, lastNow
	let snowflakes
	let maxSnowflakes = 100

	function init() {
		snowflakes = []
		resize()
		render(lastNow = performance.now())
	}

	function render(now) {
		requestAnimationFrame(render)

		const elapsed = now - lastNow
		lastNow = now
        
		ctx.clearRect(0, 0, width, height)
		if (snowflakes.length < maxSnowflakes)
			snowflakes.push(new Snowflake())

		ctx.fillStyle = ctx.strokeStyle = 'rgba(255, 255, 255, .5)'

		snowflakes.forEach(snowflake => snowflake.update(elapsed, now))
	}

	function pause() {
		cancelAnimationFrame(render)
	}
	function resume() {
		lastNow = performance.now()
		requestAnimationFrame(render)
	}


	class Snowflake {
		constructor() {
			this.spawn()
		}

		spawn(anyY = false) {
			this.x = rand(0, width)
			this.y = anyY === true
				? rand(-50, height + 50)
				: rand(-50, -10)
			this.xVel = rand(-.05, .05)
			this.yVel = rand(.02, .1)
			this.angle = rand(0, Math.PI * 2)
			this.angleVel = rand(-.001, .001)
			this.size = rand(7, 12)
			this.sizeOsc = rand(.01, .5)
		}

		update(elapsed) {
			const xForce = rand(-.001, .001);

			if (Math.abs(this.xVel + xForce) < .075) {
				this.xVel += xForce
			}

			this.x += this.xVel * elapsed
			this.y += this.yVel * elapsed
			this.angle += this.xVel * 0.05 * elapsed 

			if (
				this.y - this.size > height ||
				this.x + this.size < 0 ||
				this.x - this.size > width
			) {
				this.spawn()
			}

			this.render()
		}

		render() {
			ctx.save()
			const { x, y, size } = this
			ctx.beginPath()
			ctx.arc(x, y, size * 0.2, 0, Math.PI * 2, false)
			ctx.fill()
			ctx.restore()
		}
	}

	// Utils
	const rand = (min, max) => min + Math.random() * (max - min)

	function resize() {
		width = canvas.width = window.innerWidth
		height = canvas.height = window.innerHeight
		maxSnowflakes = Math.max(width / 10, 100)
	}

	window.addEventListener('resize', resize)
	window.addEventListener('blur', pause)
	window.addEventListener('focus', resume)
	init()

}())
    }
}
</script>

