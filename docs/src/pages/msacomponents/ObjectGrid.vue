<template>
  <page-content page-title="MSAComponents - Object Grid">
    <docs-component>
      <div slot="description">
        <p>메타데이터 서비스에서 얻어온 객체 정보를 기반으로 컬럼을 자동 구성하고 Spring Hateoas 와 JPA 를 통하여 자동으로 CRUD를 수행하는 그리드 컴포넌트입니다.</p>
      </div>

      <div slot="api">
        <api-table name="object-grid">
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
                <md-table-cell>java</md-table-cell>
                <md-table-cell><code>String</code></md-table-cell>
                <md-table-cell>메타데이터를 얻어올 자바클래스 명. e.g. <code>com.moornmo.ltms.Product</code></md-table-cell>
              </md-table-row>
              <md-table-row>
                <md-table-cell>column-changer</md-table-cell>
                <md-table-cell><code>function</code></md-table-cell>
                <md-table-cell> A callback function to be invoked when the column list has been extracted from the metadata server. In application, you may add, delete or change columns for the application-specific requirements.</md-table-cell>
              </md-table-row>
              <md-table-row>
                <md-table-cell>options</md-table-cell>
                <md-table-cell><code>Object (Map)</code></md-table-cell>
                <md-table-cell>option key-value when to render this component: keys are: <code>toolbar, sorting, editable</code></md-table-cell>
              </md-table-row>
            </md-table-body>
          </md-table>

        </api-table>

      </div>

      <div slot="example">
        <example-box card-title="Default">
          <div slot="demo">
            <img src="assets/object-grid.png"/>
          </div>

          <div slot="code">
            <code-block lang="xml">

             &lt;div id=&quot;app&quot;&gt;

                 &lt;object-grid ref=&quot;grid&quot;
                         :java=&quot;java&quot;
                         :filter-key=&quot;searchQuery&quot;
                         :column-changer=&quot;columnChanger&quot;
                         :online = &quot;true&quot;
                         :data = &quot;[]&quot;
                 &gt;
                 &lt;/object-grid&gt;

             &lt;/div&gt;

             &lt;script&gt;

                 var app = new Vue({
                     el: &apos;#app&apos;,
                     data: {
                         searchQuery: &apos;&apos;,
                         java: &quot;com.moornmo.ltms.Product&quot;,
                         data:
                             { curRestNum: 1,  optiNum: 1, props:[]},
                         columnChanger: function(columns){
                             columns.push({
                                 displayName: &apos;코드&apos;,
                                 name: &apos;code&apos;,
                                 computed: function(item){
                                     return item.prodNumber + &quot;-&quot; + item.prodName + &quot;-&quot; + item.prodStandard;
                                 }
                             })
                         }
                     }
                 })


             &lt;/script&gt;

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
