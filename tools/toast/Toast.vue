<template>
	
	<div class="toast" :class="{ fadeIn : isNotify, fadeOut : !isNotify }" v-if="onPage " >
		<div class="inner" :class="{ success : type == 'success', fail : type == 'fail', warn : type == 'warn'}" >
				<div class="content">{{msg}}</div>
		</div>
	</div>
	
</template>

<style scoped="scoped">
	
	.toast{
		position: fixed;
		width: 200px;
		height: 40px;
		top: 10%;
		left: 50%;
		transform: translate(-50%,-50%);
		color: #fff;
	}
	.success{
		background-color: #20B2AA;
	}
	.fail{
		background-color: #C9302C;
	}
	.warn{
		background-color: #20B2AA;
	}
	.inner{
		border-radius: 5px;
		box-sizing: content-box;
		width: 100%;
		height: 100%;
		line-height: 40px;
		text-align: center;
	}
	.content{
		color: #fff;
	}
	.fadeIn{
		animation: anima_fadeIn .5s ease;
	}
	.fadeOut{
		animation: anima_fadeOut .5s ease;
	}
	@keyframes anima_fadeIn{
		from{
			top: 0;
			opacity: 0;
		}
		to{
			top: 10%;
			opacity: 1;
		}
	}
	
	@keyframes anima_fadeOut{
		100%{
			top: 0;
			opacity: 0;
		}
		0%{
			top: 10%;
			opacity: 1;
		}
	}
	
</style>
