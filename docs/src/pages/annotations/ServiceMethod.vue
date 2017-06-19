<template>
  <page-content page-title="Annotations - ServiceMethod">
    <docs-component>
      <div slot="description">
        <p>POJO 객체의 일반 메서드를 REST 서비스 호출이 가능한 서비스로 생성하여 노출시켜줌. object-form 에 의하여 메서드 버튼이 자동으로 생성되고, 해당 메서드를 호출하게 연동되어 있음.</p>
      </div>

      <div slot="api">
        <api-table name="@ServiceMethod">
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
                <md-table-cell>callByContent</md-table-cell>
                <md-table-cell><code>Boolean</code></md-table-cell>
                <md-table-cell>객체의 모든 값을 전송할지 여부. false 이면 @Id 값만을 전송. whether the method call sends all the object contents from the client (browser) to the server. default is false for performance.</md-table-cell>
              </md-table-row>
              <md-table-row>
                <md-table-cell>needToConfirm</md-table-cell>
                <md-table-cell><code>Boolean</code></md-table-cell>
                <md-table-cell>해당 액션을 정말 수행할지 사용자 확인을 거친 후 진행하게 함. 주로, 삭제액션에 사용함. marks whether user need to confirm to commit this method by dialog.</md-table-cell>
              </md-table-row>
            </md-table-body>
          </md-table>

        </api-table>

      </div>

      <div slot="example">
        <example-box card-title="Default">
          <div slot="code">
            <code-block lang="java">

import org.metaworks.annotation.Face;

@Entity
@Face(displayName = "제품")
public class Product {
  @ServiceMethod(callByContent = true)
  public void validate(){
    if(getProdName()==null){
      throw new IllegalArgumentException("Prod name must be not null");
    }
  }
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
