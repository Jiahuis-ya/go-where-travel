<template>
	<div class="icon-wrapper">
		<swiper :options="swiperOption">
			<swiper-slide v-for="(page, index) of pages" :key="index">
				<div class="icon-box"
							v-for="item of page"
							:key="item.id">
						<div class="icon-img-box">
								<img class="icon-img" :src="item.imgUrl" alt="" />
						</div>
						<p class="icon-description">{{item.description}}</p>
				</div>
			</swiper-slide>
		</swiper>
	</div>
</template>

<script>
export default{
		name: 'HomeIcon',
		props: {
			iconList: Array
		},
		data: function () {
			return {
				swiperOption: {
					autoplay: false
				}
			}
		},
		computed: {
			pages: function () {
				var pages = []
				this.iconList.forEach(function (item, index) {
					var page = Math.floor(index / 8)
					if (!pages[page]) {
						pages[page] = []
					}
					pages[page].push(item)
					
				})
				
				return pages
			}
		}
}
</script>

<style lang="stylus" scoped>
@import '~styles/variables.styl'
@import '~styles/mixins.styl'


	.icon-wrapper >>> .swiper-container{
		overflow: hidden;
		width: 100%;
		height: 0;
		padding-bottom: 50%;
	}

	.icon-wrapper{
		margin: .2rem 0;
	}

	.icon-wrapper .icon-box{
		position: relative;
		float: left;
		width: 25%;
		height: 0;
		padding-bottom: 25%;
	}

	.icon-wrapper .icon-box .icon-img-box{
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		bottom: .44rem;
	}

	.icon-wrapper .icon-box .icon-img-box .icon-img{
		display: block;
		margin: 0 auto;
		height: 100%;
	}

	.icon-wrapper .icon-box .icon-description{
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		text-align: center;
		height: .44rem;
		line-height: .44rem;
		color: $darkTxtColor;
		ellipsis();
	}
</style>
