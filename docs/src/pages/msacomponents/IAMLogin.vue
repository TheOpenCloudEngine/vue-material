<template>
  <page-content page-title="MSAComponents - IAM Login">
    <docs-component>
      <div slot="description">
        <p>로그인 UI 와 함께 IAM 서버로 로그인하여 JWT 토큰을 자동으로 발급한 후, 이후 모든 AJAX 호출에 헤더를 자동으로 주입하는 컴포넌트. </p>
      </div>

      <div slot="api">
        <api-table name="iam-login">
          <md-table slot="properties">
            <md-table-header>
              <md-table-row>
                <md-table-head>Name</md-table-head>
                <md-table-head>Type</md-table-head>
                <md-table-head>Description</md-table-head>
              </md-table-row>
            </md-table-header>

            <md-table-body>
              <md-table-row>
                <md-table-cell>iam-server</md-table-cell>
                <md-table-cell><code>String</code></md-table-cell>
                <md-table-cell>IAM 로그인을 할 uEngine IAM 서버. <code>iam.uengine.io:9090</code></md-table-cell>
              </md-table-row>
              <md-table-row>
                <md-table-cell>api-key</md-table-cell>
                <md-table-cell><code>String</code></md-table-cell>
                <md-table-cell>uEngine IAM 서버에 등록된 client key. <a href="https://github.com/TheOpenCloudEngine/uEngine-iam"></a> 참조.</md-table-cell>
              </md-table-row>
              <md-table-row>
                <md-table-cell>options</md-table-cell>
                <md-table-cell><code>Object (Map)</code></md-table-cell>
                <md-table-cell></md-table-cell>
              </md-table-row>
            </md-table-body>
          </md-table>

        </api-table>

      </div>

      <div slot="example">
        <example-box card-title="Default">
          <div slot="demo">
          </div>

          <div slot="code">
            <code-block lang="xml">&lt;iam-login iam-server=&quot;http://iam.uengine.io:8080&quot; api-key=&quot;e74a9505-a811-407f-b4f6-129b7af1c703&quot; &gt;&lt;/iam-login&gt;</code-block>
          </div>
        </example-box>

      </div>
    </docs-component>
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
