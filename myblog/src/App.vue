<style scoped>
.layout {
  border: 1px solid #d7dde4;
  background: #fff;
  position: relative;
  border-radius: 4px;
  overflow: hidden;
}
.layout-nav {
  width: 20%;
  margin-left: 40%;
}
</style>
<template>
  <Scroll :on-reach-edge="handleReachEdge">
    <div class="layout" :style="{height:'1080px'}">
      <div>
        <Menu mode="horizontal" theme="dark" active-name="1">
          <!-- <div class="layout-logo"></div> -->
          <div class="layout-nav">
            <MenuItem name="1">
              <Icon type="md-paper" />文章
            </MenuItem>
            <MenuItem name="2">
              <Icon type="md-link" />便签墙
            </MenuItem>
          </div>
        </Menu>
      </div>

      <!-- <div :style="{padding: '24px',width:'80vh',margin:'0 500px'}"> -->
      <!-- <div v-for="item in 10" :key="item" :style="{padding: '24px', background: '#fff',width:'80vh',height:'50vh',margin:'10px 0'}">
                  {{item}}
      </div>-->
      <div
        v-for="item in 10"
        :key="item"
        :style="{padding: '24px', background: '#fff',width:'80vh',margin:'10px 0'}"
      >{{item}}
      </div>

      <div :style="{margin: '0'}">
        <Card :style="{position: 'fixed',margin:'50px 0'}">
          <p slot="title">The standard card</p>
          <p>Content of card</p>
          <p>Content of card</p>
          <p>Content of card</p>
        </Card>
      </div>
      <!-- </div> -->
    </div>
  </Scroll>
</template>
<script>
export default {
  data() {
    return {
      list3: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    };
  },
  methods: {
    handleReachEdge(dir) {
      return new Promise(resolve => {
        setTimeout(() => {
          if (dir > 0) {
            const first = this.list3[0];
            for (let i = 1; i < 11; i++) {
              this.list3.unshift(first - i);
            }
          } else {
            const last = this.list3[this.list3.length - 1];
            for (let i = 1; i < 11; i++) {
              this.list3.push(last + i);
            }
          }
          resolve();
        }, 2000);
      });
    }
  }
};
</script>
js 无限滚动
div 布局