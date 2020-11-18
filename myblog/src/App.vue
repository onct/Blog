<template>
  <div id="app">
    <div class="bgimg panel-main" :style="{backgroundImage: 'url( '+ bgurl +')'}">
      <div class="coverpannel"></div>
      <div v-if="windowWidth < 980" >
        <span  class="el-dropdown-link">
          <i width="windowWidth" class="el-icon-arrow-down el-icon-menu"></i>
        </span>
      </div>
      <div>
        <img class="headicon" src="@/assets/img/gravtor.jpg" />
      </div>
      <h1>
        <a href>Miaode</a>
      </h1>
      <div>
        <label class="typed">
          {{obj.output}}
          <span>|</span>
        </label>
      </div>
      <div class="divider"></div>
      <p class="description">嗨，我是 Miaode，来自三次元的魔法师，目前暂驻于天津，秃头学院，软件工程专业。</p>
      <div class="divider" style="width: 10%"></div>

      <p class="description">欢迎来到我的世界!</p>

      <div>
        <nav v-if="windowWidth > 980">
          <ul>
            <li class="navigation__item">
              <a href="" title="访问博客">博客</a>
            </li>
            <li class="navigation__item">
              <a href="https://img.ffis.me/" target="_blank" title="饭饭's 图床">图床</a>
            </li>
            <li class="navigation__item">
              <a href="https://sign.ffis.me/" title="饭饭's 签到站">签到站</a>
            </li>
            <li class="navigation__item">
              <a href="https://dl.ffis.me/" title="饭饭's 下载站">下载站</a>
            </li>
            <li class="navigation__item">
              <a href="https://ffis.me/about.html" title="关于饭饭">关于</a>
            </li>
          </ul>
        </nav>
      </div>
      <!-- 底部年份动态化 + 备案号 -->
      <footer class="footer">
        <p>
          &copy;{{year}}
          yiman.xyz |
          <a
            style="TEXT-DECORATION: none"
            href="http://www.miibeian.gov.cn"
            rel="nofollow"
            target="_blank"
          >
            <font color="#b3b3b3">豫ICP备16034017号-1</font>
          </a>
        </p>
      </footer>
    </div>
    <div class="panel-cover--overlay cover-slate"></div>
  </div>
</template>

<script>
import EasyTyper from "easy-typer-js";

export default {
  name: "App",
  data() {
    return {
      windowWidth: document.documentElement.clientWidth, //实时屏幕宽度
      windowHeight: document.documentElement.clientHeight, //实时屏幕高度
      bg: [
        require("@/assets/img/background-image/bg-0.jpg"),
        require("@/assets/img/background-image/bg-1.jpg"),
        require("@/assets/img/background-image/bg-2.jpg"),
        require("@/assets/img/background-image/bg-3.jpg"),
        require("@/assets/img/background-image/bg-4.jpg"),
        require("@/assets/img/background-image/bg-5.jpg"),
        require("@/assets/img/background-image/bg-6.jpg"),
        require("@/assets/img/background-image/bg-7.jpg"),
        require("@/assets/img/background-image/bg-8.jpg"),
        require("@/assets/img/background-image/bg-9.jpg"),
        require("@/assets/img/background-image/bg-10.jpg")
      ],
      bgurl: "",
      year: "",
      obj: {
        output: "",
        isEnd: false,
        speed: 160,
        singleBack: false,
        sleep: 50,
        type: "rollback",
        backSpeed: 80,
        sentencePause: false
      }
    };
  },
  methods: {
    // 初始化
    init() {
      this.fetchData();
    },
    fetchData() {
      fetch("https://v1.hitokoto.cn")
        .then(res => {
          return res.json();
        })
        .then(({ hitokoto }) => {
          this.initTyped(hitokoto);
        })
        .catch(err => {
          console.error(err);
        });
    },

    initTyped(input, fn, hooks) {
      const obj = this.obj;
      const typed = new EasyTyper(
        obj,
        input,
        () => {
          // 回调函数，easyTyper生命周期结束后执行
          this.initTyped(input);
        },
        hooks
      );
    }
  },
  // <!--在watch中监听实时宽高-->
  watch: {
    windowHeight(val) {
      let that = this;
    },
    windowWidth(val) {
      let that = this;
    }
  },

  mounted() {
    // <!--把window.onresize事件挂在到mounted函数上-->
    window.onresize = () => {
      return (() => {
        window.fullHeight = document.documentElement.clientHeight;
        window.fullWidth = document.documentElement.clientWidth;
        that.windowHeight = window.fullHeight; // 高
        that.windowWidth = window.fullWidth; // 宽
      })();
    };
    this.init();
    var that = this;
    this.year = new Date().getFullYear();
    let randomBgIndex = Math.round(Math.random() * 10);
    this.bgurl = this.bg[randomBgIndex];
  }
};
</script>

<style>
/* .el-header {
  background-color: #d3dce6;
  color: #333;
  text-align: center;
}
.el-footer {
  background-color: #d3dce6;
  color: #333;
  text-align: center;
}
.el-main {
  background-color: #e9eef3;
  color: #333;
  text-align: center;
} */
body {
  margin: 0;
}
.panel-main {
  text-align: center;
  text-shadow: 0 1px 1px rgba(0, 0, 0, 0.4);
  font-weight: 100;
}
.coverpannel {
  background-color: #1c2727bf;
  opacity: 0.7;
  z-index: -1;
  width: 100%;
  height: 100%;
  position: absolute;
}
.headicon {
  margin-top: 3%;
  width: 6%;
  z-index: 1;
  border: 3px solid #d0d0d0;
  border-radius: 50%;
  box-shadow: 0 0 1px 1px rgba(0, 0, 0, 0.3);
  transition: all 0.5s;
}

.headicon:hover {
  border: 3px solid #5ba4e5;
  transition: all 0.5s;
  transform: rotate(360deg);
}

.bgimg {
  position: fixed;
  width: 100%;
  height: 100%;
  max-width: none;
  background: top left no-repeat #666666;
  background-size: cover;
}
.divider {
  margin: 2% auto;
  width: 15%;
  border-top: 1px solid rgb(204, 204, 204);
}
a {
  color: #fff;
  font-weight: 300;
  text-decoration: none;
}
.description {
  letter-spacing: 3px;
  color: #d0d0d0;
  width: 40%;
  left: 30%;
  position: relative;
  text-align: center;
  font-weight: 400;
}
nav {
  margin-top: 8%;
  position: relative;
  display: inline-block;
}

.navigation__item {
  display: inline-block;
  margin: 5px 5px 0 0;
  line-height: 1em;
}
.navigation__item a {
  position: relative;
  display: block;
  color: #fff;
  opacity: 0.8;
  padding: 10px 20px;
  border: 1px solid #ffffff;
  border-radius: 20px;
  text-shadow: none;
  letter-spacing: 1px;
  font-weight: bold;
  font-size: 0.9em;
  -webkit-font-smoothing: antialiased;
}
.footer {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  color: #b3b3b3;
  font-size: 0.7em;
}
.typed {
  letter-spacing: 3px;
  color: #d0d0d0;
  width: 40%;
  left: 40%;
  text-align: center;
  font-weight: 400;
}
.el-dropdown-link {
  cursor: pointer;
  opacity: 0.7;
  
  color: #409EFF;
}
.el-icon-arrow-down {
  font-size: 12px;
  background-color: lightslategray;
  width: 900px;
}
</style>