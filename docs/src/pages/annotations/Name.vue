<template>
  <page-content page-title="Annotations - Id and Name">
    <docs-component>
      <div slot="description">
        <p>어떤 객체를 구분하는 Id 와 대표격 이름을 가진 이름 필드를 지정</p>
      </div>

            <code-block lang="java">

@Entity
@Table(name = "TB_PROD")
@Face(displayName = "제품")
public class Product{

  @Id //pNo 는 JPA 에서의 primary key 임.
  @GeneratedValue(strategy = GenerationType.AUTO)
  Long pNo;
  @Hidden //화면에 나타나지 않게
  @org.metaworks.annotation.Id //pNo 는 mw4 에서의 객체 구분자임.
  public Long getpNo() {
   return pNo;
  }
  public void setpNo(Long pNo) {
    this.pNo = pNo;
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
