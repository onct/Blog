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
  <div class="layout">
    <Layout>
      <Header>
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
      </Header>
      <Layout>
        <Layout :style="{height:'93vh',padding: '0 24px 24px'}">
          <Content :style="{padding: '24px', background: '#fff',width:'500px'}">Content</Content>
        </Layout>
        <Sider hide-trigger :style="{background: '#f5f7f9'}">
           <Card :style="{position: 'fixed',margin:'50px 0'}">
                <p slot="title">The standard card</p>
                <p>Content of card</p>
                <p>Content of card</p>
                <p>Content of card</p>
            </Card>
        </Sider>
      </Layout>
    </Layout>
  </div>
</template>
<script>
export default {};
</script>
