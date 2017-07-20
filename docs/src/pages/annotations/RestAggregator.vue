

<template>
  <page-content page-title="Annotations - RestAggregator">
    <docs-component>
      <div slot="description">
        <p>REST 로 연결된 참조 데이터를 path 로 지정하여 클라이언트에서 Lazy Loading 하게 해줌. HATEOAS Spec 에 따라 _links 에 lazy loading 될 url 을 생성시켜줌. 멀티테넌트 데이터나 고객사별 특화된 연동 데이터를 연결할 때 사용함. </p>
      </div>



      <code-block lang="java">
@Transient
@RestAggregator(
  path = "/pools/default/buckets/default/docs/{{ '{'+'{tenantId}'+'}/{'+'{entity.name}'+'}/{'+'{@id}'+'}' }}",
  role = "http://localhost:8091"
)
TenantProperties tenantProperties;
  @Hidden
  public TenantProperties getTenantProperties() {
    return tenantProperties;
  }
  public void setTenantProperties(TenantProperties tenantProperties) {
    this.tenantProperties = tenantProperties;
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
