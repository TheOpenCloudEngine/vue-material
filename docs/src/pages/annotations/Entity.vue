

<template>
  <page-content page-title="Annotations - Entity and Table">
    <docs-component>
      <div slot="description">
        <p>도메인 객체가 JPA 를 통하여 저장 가능한 객체임을 지정하여 ORM 자동화가 가능하도록 표시함. </p>
      </div>



      <code-block lang="java">

import javax.persistence.*;

@Entity
@Table(name = "TB_PROD")
public class Product {
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
