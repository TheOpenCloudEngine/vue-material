

<template>
  <page-content page-title="Annotations - JoinColumn, OneToMany, ManyToOne and ManyToMany">
    <docs-component>
      <div slot="description">
        <p>Entity Class 필드가 Foreign table 에 의하여 참조될 때 관계 정보를 제공함.</p>
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
