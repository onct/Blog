<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<script src="vue.js"></script>
		<link rel="stylesheet" type="text/css" href="index.css" />
		<script src="index.js"></script>
		<title></title>
	</head>
	<body>
		<div id="app">
			<el-container >
				<el-header>
					<el-menu :default-active="'1'" mode="horizontal" background-color="#545c64" text-color="#fff" active-text-color="#ffd04b">
						<el-menu-item index="1">文章</el-menu-item>
						<el-menu-item index="2">便簽墻</el-menu-item>
					</el-menu>
				</el-header>
				<el-container style="height: 500px;">
					<el-main  v-infinite-scroll="load" infinite-scroll-disabled="busy" infinite-scroll-distance="10">
						<div v-for="i in count" :key="i" class="article">
							<el-card :body-style="{ height: '180px' }" shadow="hover">
								<div class="article-head">
									<span>{{title}}</span>
									<span>{{title}}</span>
								</div>
								<hr>
								<div class="article-text">
									{{content}}
								</div>
							</el-card>
						</div>

					</el-main>
					<el-aside width="20%">
						<el-card class="box-card">

							<el-image></el-image>
						</el-card>

						<el-card class="box-card">
							<div slot="header" class="clearfix">
								<span>卡片名称</span>
							</div>
							<div v-for="o in 4" :key="o" class="text item">
								{{'列表内容 ' + o }}
							</div>
						</el-card>

						<el-card class="box-card">
							<div slot="header" class="clearfix">
								<span>卡片名称</span>
							</div>
							<div v-for="o in 4" :key="o" class="text item">
								{{'列表内容 ' + o }}
							</div>
						</el-card>
					</el-aside>

				</el-container>
				<el-footer>
					<div style="height: 20px;"><span>loading </span></div>
					</el-footer>
			</el-container>
		</div>
	</body>

	<script>
		new Vue({
			el: '#app',
			data: {
				title:"test",
				content:"df;lshglkjshen;lkjbnlknf;jbinhs;fgnaewrogbegbdfkjvbn",
				message: 'Hello Vue.js!',
				count: 0,
				busy: false
			},
			methods: {
			      load () {
					this.busy = true
					setTimeout(() => {
					for (var i = 0, j = 3; i < j; i++) {
					  this.count++
					}
					console.log(this.count)
					this.busy = false
				  }, 1000)
			      }
			    }
		})
	</script>
	<style type="text/css">
		.box-card {
			margin-top: 5%;
		}

		.el-header,
		.el-footer {
			text-align: center;
			line-height: 60px;
		}


		.el-main {
			text-align: center;
		}

		.article {
			margin: 2%;
			text-align: start;
		}

		.article-head {
			line-height: 20px;
		}

		.article-text {
			line-height: 60%;
		}
	</style>
</html>
