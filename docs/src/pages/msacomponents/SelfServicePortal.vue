<template>
  <page-content page-title="MSAComponents - IAM Login">
      <div slot="description">
        <p>현재 로그인된 유저의 가입 테넌트 ID 를 통하여 셀프서비스 포탈의 UI를 제공함.</p>
        <p>Dependency: iam-login tag 를 이용하여 IAM 서버를 통하여 로그인 처리되어야 테넌트를 식별할 수 있음.</p>
      </div>
        <div slot="code">
          <code-block lang="xml">&lt;self-service-portal &gt;&lt;/self-service-portal&gt;</code-block>
        </div>
  </page-content>
</template>

<style lang="sass" scoped>
  .md-bottom-bar {
    position: absolute;
    right: 0;
    bottom: 0;
    left: 0;
  }

  .phone-viewport {
    width: 320px;
    height: 150px;
    margin-right: 16px;
    display: inline-block;
    position: relative;
    overflow: hidden;
    background-color: darken(#fafafa, 5%);
  }
</style>

<script>
  export default {
    data() {
      return {
        playground: {
          theme: 'brown'
        }
      };
    },
    methods: {
      setTheme(theme) {
        this.playground.theme = theme;
      }
    }
  };
</script>
