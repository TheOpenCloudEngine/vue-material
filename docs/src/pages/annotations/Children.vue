

<template>
  <page-content page-title="Annotations - Children">
    <docs-component>
      <div slot="description">
        <p>객체가 트리 구조를 가진 경우, 하위 자식 노드에 해당하는 필드나 getter 메서드를 지정. Tree GUI 를 생성할 때 사용.</p>
      </div>

      <div slot="example">
        <example-box card-title="Default">
          <div slot="code">

            <code-block lang="html">
              &lt;object-tree java=&quot;com.moornmo.ltms.Product&quot;&gt;&lt;/object-tree&gt;

            </code-block>

            <code-block lang="java">

import org.metaworks.annotation.Children;

@Entity
@Face(displayName = "제품")
public class Product {

  List&lt;Product&gt; childProds;
  @Children
  @Face(displayName = "하위제품")
  public List&lt;Product&gt; getChildProds() {
   return childProds;
  }
  public void setChildProds(List&lt;Product&gt; childProds) {
   this.childProds = childProds;
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
