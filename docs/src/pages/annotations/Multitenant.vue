

<template>
  <page-content page-title="Annotations - Multitenant">
    <docs-component>
      <div slot="description">
        <p>JPA Entity 객체인 경우 멀티테넌시로 분리된 테이블(스키마) 혹은 분리된 컬럼에 의하여 저장되어야 하는 경우를 지정. </p>
      </div>



      <code-block lang="java">
import org.eclipse.persistence.annotations.Multitenant;
import org.eclipse.persistence.annotations.TenantDiscriminatorColumn;
import org.metaworks.annotation.*;

import javax.persistence.*;

@Multitenant
@TenantDiscriminatorColumn(name = "TENANTID", contextProperty = "tenant-id")
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
