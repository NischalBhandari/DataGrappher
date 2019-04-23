<template>
	<div>
<div class="btn" @click="moveX" @keyup.space="moveX" tabindex="0">Move in X+</div>
<div class="btn" @click="moveY">Move in Y</div>
<div class="btn" @click="moveXneg">Move in X-</div>
<div class="btn" @click="moveYneg">Move in Y-</div>
	<svg v-bind:width="width" v-bind:height="height">
<circle v-bind:cx="xpos" v-bind:cy="ypos" v-bind:r="radii"></circle>
<circle v-bind:cx="secondxpos" v-bind:cy="ypos" v-bind:r="radii"></circle>
<circle v-bind:cx="xpos" v-bind:cy="secondypos" v-bind:r="radii"></circle>
<circle v-bind:cx="secondxpos" v-bind:cy="secondypos" v-bind:r="radii"></circle>
</svg>
</div>
</template>


<script>
	export default{
		name: "picker",
		data(){
			return {
				width: '300',
				height: '300',
				xpos : '0',
				ypos : '0',
				radii : '70',
				secondxpos:'-100',
				secondypos: '-100',
				xtemp: '',
				ytemp: ''
			}
		},
		methods: {
			moveX(){
				this.xpos = `${parseFloat(this.xpos) + 10}`;
				this.secondxpos = `${parseFloat(this.xpos) - parseFloat(this.width)}`
				if(parseFloat(this.xpos) >= (parseFloat(this.width) + 2 * parseFloat(this.radii)) )
				{
					this.xtemp = this.xpos
					this.xpos = this.secondxpos
					this.xtemp = ''
				}
			},
			moveY(){
				this.ypos = `${parseFloat(this.ypos)+10}`;
				this.secondypos = `${parseFloat(this.ypos) - parseFloat(this.height)}`
				if(parseFloat(this.ypos) >= (parseFloat(this.height) + 2 * parseFloat(this.radii)) )
				{
					this.ytemp = this.ypos
					this.ypos = this.secondypos
					this.xyemp = ''
				}
			},
			moveXneg(){
				this.xpos = `${parseFloat(this.xpos) - 10}`;
				this.secondxpos = `${parseFloat(this.xpos) + parseFloat(this.width)}`
				if(parseFloat(this.xpos) <= ((2 * parseFloat(this.radii)) - parseFloat(this.width) ))
				{
					this.xtemp = this.xpos
					this.xpos = this.secondxpos
					this.xtemp = ''
				}
			

			},
			moveYneg(){
				this.ypos = `${parseFloat(this.ypos) - 10}`;
				this.secondypos = `${parseFloat(this.ypos) + parseFloat(this.height)}`
				if(parseFloat(this.ypos) <= ((2 * parseFloat(this.radii)) - parseFloat(this.height) ))
				{
					this.ytemp = this.ypos
					this.ypos = this.secondypos
					this.ytemp = ''
				}

			}
		}

	}
	
</script>

<style scoped>
.cicrle{
	fill: transparent;
	stroke: #fff;

}
.btn{


}
	
</style>