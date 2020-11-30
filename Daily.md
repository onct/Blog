<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<script src="vue.js"></script>
		<link rel="stylesheet" type="text/css" href="index.css" />
		<script src="index.js"></script>
		<title></title>
	</head>
	<style type="text/css">
		.main{
			display: flex;
			flex-wrap: wrap;
			justify-content: center;
		}
		.menu{
			width: 100%;
		}
		.card1{
			width: 12%;
			height: 25%;
			position: fixed;
			margin-left:42%;
			margin-top: 8%;
		}
		.card2{
			width: 12%;
			height: 25%;
			position: fixed;
			margin-left:42%;
			margin-top: 25%;
		}
		.article{
			width: 51%;
			height: 17%;
			margin-top: 2%;
			padding: 15px;
			border: 1px solid #d7dde4;
			background: #fff;
			position: relative;
			border-radius: 4px;
			font-size: 14px;
			font-family: tahoma,arial,"Microsoft YaHei","Hiragino Sans GB","\5b8b\4f53",sans-serif;
		}
		.article-text{
			overflow: visible;
			word-wrap: break-word;
			line-height: 28px;
			padding-bottom: 5px;
		}
		.article-href{
			color: #999;
			font-size: .9em;
			margin: 10px 0;
		}
		
	</style>
	<body>
		<div  id="app" class="main" :style="{height:'1080px'}">
			<div class="menu">
				<el-menu :default-active="'1'" mode="horizontal" background-color="#545c64" text-color="#fff" active-text-color="#ffd04b">
					<el-menu-item style=" margin-left:40%;" index="1">文章</el-menu-item>
					<el-menu-item index="2">便簽墻</el-menu-item>
				</el-menu>
			</div>
			
			<div v-for="i in count" :key="i" class="article">
					<h3>	
					{{title}}{{i}}
					</h3>
					<div class="article-href">
						
					分類:<span style="color: #409EFF;">{{title}}</span> <!-- vue router -->
					/ 時間:<span style="color: #409EFF;">{{title}}</span>
					</div>
					<div class="article-text">
						{{content}}
					</div>
					<div class=".article-href">
						顯示剩餘
					</div>
			</div>
		
			
					
			<el-card class="card1">
				<div slot="header" class="clearfix">
					<span>卡片名称</span>
				</div>
				<div v-for="o in 4" :key="o" class="text item">
					{{'列表内容 ' + o }}
				</div>
			</el-card>
					
			<el-card class="card2">
				<div slot="header" class="clearfix">
					<span>卡片名称</span>
				</div>
				<div v-for="o in 4" :key="o" class="text item">
					{{'列表内容 ' + o }}
				</div>
			</el-card>
		</div>
	</body>

	<script>
		new Vue({
			el: '#app',
			data: {
				title:"test這是我一生中最勇敢的瞬間",
				content:"這是我一生中最勇敢的瞬間這是我一生中最勇敢的瞬間這是我一生中最勇敢的瞬間這是我一生中最勇敢的瞬間這是我一生中最勇敢的瞬間這是我一生中最勇敢的瞬間這是我一生中最勇敢的瞬間這是我一生中最勇敢的瞬間這是我一生中最勇敢的瞬間這是我一生中最勇敢的瞬間這是我一生中最勇敢的瞬間這是我一生中最勇敢的瞬間這是我一生中最勇敢的瞬間這是我一生中最勇敢的瞬間這是我一生中最勇敢的瞬間這是我一生中最勇敢的瞬間this is the bravest time in my life,this is the bravest time in my life，this is the bravest time in my life，this is the bravest time in my life這是我一生中最勇敢的瞬間this is the bravest time in my lifethis is the bravest time in my life這是我一生中最勇敢的瞬間",
				message: 'Hello Vue.js!',
				count: 0,
				busy: false,
			},
			methods: {
				// axios请求接口获取数据
				getInitialUsers() {
					for (var i = 0; i < 5; i++) {
						// axios.get(`https://randomuser.me/api/`).then(response => {
						//   this.persons.push(response.data.results[0])
						// })
						this.count += 1
					}
				},
				formatDate(date) {
					if (date) {
						return moment(String(date)).format('MM/DD/YYYY')
					}
				},
			
				scroll(person) {
					let isLoading = false
					window.onscroll = () => {
						// 距离底部200px时加载一次
						// let bottomOfWindow = document.documentElement.offsetHeight - document.documentElement.scrollTop - window.innerHeight <=
						// 	0
						
						var height = document.documentElement.offsetHeight
						if (document.documentElement.offsetHeight <= document.documentElement.scrollTop)
							bottomOfWindow = 0.2*height*this.count -document.documentElement.scrollTop<= 100
						else
							bottomOfWindow = height - document.documentElement.scrollTop - window.innerHeight <= 0
						console.log(0.2*height*this.count)
						if (bottomOfWindow && isLoading == false) {
							isLoading = true
							this.count += 1
							isLoading = false
							//     axios.get(`https://randomuser.me/api/`).then(response => {
							// person.push(response.data.results[0])
							// this.persons+=2
							//       isLoading = false
							//     })
						}
					}
				}
			},
			
			beforeMount() {
				// 在页面挂载前就发起请求
				this.getInitialUsers()
			},
			mounted() {
				this.scroll(this.count)
			}
		})
	</script>
</html>
