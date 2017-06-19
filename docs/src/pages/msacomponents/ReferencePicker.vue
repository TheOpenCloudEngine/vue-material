<template>
  <page-content page-title="DDD/MSA Components - Reference Picker">
    <docs-component>
      <div slot="description">
        <p>참조 키 값의 목록 값을 얻어와 선택할 수 있도록 해주는 셀렉트 컴포넌트.</p>
      </div>

      <div slot="api">
        <api-table name="reference-picker">
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
                <md-table-cell>options</md-table-cell>
                <md-table-cell><code>Object (Map)</code></md-table-cell>
                <md-table-cell>option key-value when to render this component: keys are: <code>class</code></md-table-cell>
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
            <code-block lang="xml">



            </code-block>
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
