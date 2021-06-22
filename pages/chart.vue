<template>
	<div>
		<section class="hero is-danger">
			<div class="hero-body">
				<p class="title">
					<i class="fas fa-futbol"></i> 맨체스터 유나이티드의 역대 성적					
				</p>
				<p class="subtile">
					맨체스터 유나이티드의 이적료 통계를 시각적으로 보여줍니다.
				</p>
			</div>
		</section>
		<hr />
		<section class="columns">
			<div class="column">
				<article class="message">
					<div class="message-header">
						역대 순위
					</div>
					<div class="message-body">
						<div
							id="lineChart"
							:style="`width:100%;height:${chartHeight}px`"
						></div>
						<div class="content">
							<p class="tag is-danger">출처</p>
							<a href="https://www.manutd.com/ko">
								맨체스터 유나이티드 공식 홈페이지</a
							>
						</div>
					</div>
				</article>
			</div>
			<div class="column">
				<article class="message">
					<div class="message-header">
						이적료 순위
					</div>
					<div class="message-body">
						<div id="pieChart" style="width:100%;height:400px"></div>
						<div class="content">
							<p class="tag is-danger">출처</p>
							<a href="https://www.manutd.com/ko">
								맨체스터 유나이티드 공식 홈페이지</a
							>
						</div>
					</div>
				</article>
			</div>
		</section>
	</div>
</template>
<script>
	import toastuiChart from '~/plugins/toastuiChart';
	let showChart = false;
	const playerMoney = {
		categories: [
			'06-07 시즌',
			'07-08 시즌',
			'08-09 시즌',
			'09-10 시즌',
			'10-11 시즌',
			'11-12 시즌',
			'12-13 시즌',
			'13-14 시즌',
			'14-15 시즌',
			'15-16 시즌',
			'16-17 시즌',
			'17-18 시즌',
			'18-19 시즌',
			'19-20 시즌',
			'20-21 시즌',
		], // y-axis
		series: [
			// x-axis
			{
				name: '프리미어리그',
				data: [1, 1, 1, 2, 1, 2, 1, 7, 4, 5, 6, 2, 6, 3, 2],
			},
			{
				name: '챔피언스리그',
				data: [4, 1, 2, 8, 2, 0, 16, 8, 0, 0, 0, 16, 8, 0, 0],
			},
			{
				name: '유로파리그',
				data: [0, 0, 0, 0, 0, 16, 0, 0, 0, 16, 1, 0, 0, 4, 2],
			},
			{
				name: 'FA 컵',
				data: [2, 8, 4, 64, 4, 32, 8, 64, 8, 1, 8, 2, 8, 4, 8],
			}	
		],
	};
	const Money = {
		categories: ['이적료'],
		series: [
			{
				name: '폴 포그바',
				data: 105.0,
			},
			{
				name: '해리 매과이어',
				data: 87.0,
			},						
			{
				name: '앙토니 마샬',
				data: 60.0,
			},
			{
				name: '프레드',
				data: 59.0,
			},			
			{
				name: '리오 퍼디난드',
				data: 46.0,
			},
			{
				name: '후안 마타',
				data: 44.7,
			},			
		],
	};
	export default {
		data() {
			return { chartHeight: 400 };
		},
		mounted() {
			if (!showChart && process.client) {
				if (!toastuiChart('bar', 'lineChart', playerMoney)) return;
				if (!toastuiChart('pie', 'pieChart', Money)) return;
				showChart = true;
			}
		},
		destroyed() {
			showChart = false;
		},
	};
</script>