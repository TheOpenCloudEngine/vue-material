<template>
  <page-content page-title="Annotations - Face">
    <docs-component>
      <div slot="description">
        <p>객체와 프로퍼티, 그리고 메서드에 대한 화면 출력에 관한 메타데이터 정의 어노테이션입니다.</p>
      </div>

      <div slot="api">
        <api-table name="@Face">
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
                <md-table-cell>displayName</md-table-cell>
                <md-table-cell><code>String</code></md-table-cell>
                <md-table-cell>객체에 대한 화면 출력 메시지. 클래스 선언부, 프로퍼티(getter 위에 넣어야 함) 선언부, 메서드 선언부 위에 주입해준다.</md-table-cell>
              </md-table-row>
              <md-table-row>
                <md-table-cell>options and values</md-table-cell>
                <md-table-cell><code>String Array</code></md-table-cell>
                <md-table-cell>Vue UI Component 로 전달할 확장 옵션 key 와 value. 배열 값으로 전달함. 예를 들어 옵션으로 <code>vue-component</code> 는, 값으로 vue component element 명을 주면, 선택하는 UI 로 필드 입력 컨트롤을 구성한다. (예를 들어, <code>reference-picker</code>를 주면 DB에서 값을 찾아 선택하는 UI 로 필드 입력 컨트롤을 구성한다.)</md-table-cell>
              </md-table-row>
            </md-table-body>
          </md-table>

        </api-table>

      </div>

      <div slot="example">
        <example-box card-title="Display Name">
          <div slot="code">
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

}

            </code-block>
          </div>
        </example-box>

        <example-box card-title="Vue component setting">
          <div slot="code">
            <code-block lang="java">

@JoinColumn(name = "prodId") // Normally reference-picker will be used together with @JoinColumn of JPA
Product product;
  @Face(options = {"class", "vue-component"}, values = {"com.moornmo.ltms.Product", "reference-picker"})
  public Product getProduct() {
    return product;
  }
  public void setProduct(Product product) {
    this.product = product;
  }

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
