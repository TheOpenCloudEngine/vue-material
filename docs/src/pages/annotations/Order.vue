<template>
  <page-content page-title="Annotations - Order">
    <docs-component>
      <div slot="description">
        <p>필드의 출력 순서. 그리드나 폼에 나열될 순서로 사용됨.</p>
      </div>

      <div slot="api">
        <api-table name="@Order">
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
                <md-table-cell>value</md-table-cell>
                <md-table-cell><code>Integer</code></md-table-cell>
                <md-table-cell>필드의 출력 순서. 그리드나 폼에 나열될 순서로 사용됨. The order of field. The value will be used for aligning grid columns and form fields.</md-table-cell>
              </md-table-row>
            </md-table-body>
          </md-table>

        </api-table>

      </div>

            <code-block lang="java">

import org.metaworks.annotation.Face;

@Entity
@Face(displayName = "제품")
public class Product {

  String prodNumber;
  @Face(displayName = "품번(제품코드)")
  @Order(10)
    public String getProdNumber() {
      return prodNumber;
    }
    public void setProdNumber(String prodNumber) {
      this.prodNumber = prodNumber;
    }

  String prodName;
  @Face(displayName = "품명")
  @Order(20)
  @Name
    public String getProdName() {
      return prodName;
    }
    public void setProdName(String prodName) {
      this.prodName = prodName;
    }

}

            </code-block>
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
