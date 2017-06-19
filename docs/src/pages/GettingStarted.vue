<template>
  <page-content page-title="Getting Started">
    <div class="main-content">
      <article>
        <section>
          <h2 class="md-headline">프론트 엔드</h2>

          <p>프론트 엔드</p>
          <code-block lang="html">

&lt;div id=&quot;app&quot;&gt;

    &lt;object-grid ref=&quot;grid&quot;
            :java=&quot;java&quot;
            :filter-key=&quot;searchQuery&quot;
            :column-changer=&quot;columnChanger&quot;
            :online = &quot;true&quot;
            :data = &quot;[]&quot;
            :options=&quot;{pagination: true, toolbar: true}&quot;
    &gt;
    &lt;/object-grid&gt;

    &lt;md-button class=&quot;md-fab md-fab-bottom-right&quot; id=&quot;fab&quot; @click.native=&quot;$refs[&apos;dialog&apos;].open()&quot;&gt;
        &lt;md-icon&gt;add&lt;/md-icon&gt;
    &lt;/md-button&gt;

    &lt;md-dialog md-open-from=&quot;#fab&quot; md-close-to=&quot;#fab&quot; ref=&quot;dialog&quot;&gt;
        &lt;md-dialog-title&gt;제품 마스터 생성&lt;/md-dialog-title&gt;

        &lt;md-dialog-content&gt;
            &lt;object-form ref=&quot;object-form&quot;
                    :java=&quot;java&quot;
                    :data = &quot;data&quot;
                    :event-listeners = &quot;[&apos;grid&apos;]&quot;
            &gt;
            &lt;/object-form&gt;
        &lt;/md-dialog-content&gt;

        &lt;md-dialog-actions&gt;
            &lt;md-button class=&quot;md-primary&quot; @click.native=&quot;$refs[&apos;object-form&apos;].submit_(); $refs[&apos;dialog&apos;].close()&quot;&gt;저장&lt;/md-button&gt;
            &lt;md-button class=&quot;md-primary&quot; @click.native=&quot;$refs[&apos;dialog&apos;].close()&quot;&gt;닫기&lt;/md-button&gt;
        &lt;/md-dialog-actions&gt;
    &lt;/md-dialog&gt;
&lt;script&gt;
    $( function() {
        $(&apos;table tbody&apos;).sortable();
        $(&apos;table tbody&apos;).disableSelection();
    } );
&lt;/script&gt;
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


&lt;/script&gt;          </code-block>
        </section>
      </article>

      <article>
        <h2 class="md-headline">백-엔드 개발</h2>

        <section>
          <p>도메인 클래스 선언:</p>
          <code-block lang="java">
package com.moornmo.ltms;

import com.fasterxml.jackson.annotation.JsonAnyGetter;
import com.fasterxml.jackson.annotation.JsonAnySetter;
import com.fasterxml.jackson.annotation.JsonUnwrapped;
import com.moornmo.framework.AfterLoad;
import com.moornmo.framework.BeforeSave;
import org.eclipse.persistence.annotations.Multitenant;
import org.eclipse.persistence.annotations.TenantDiscriminatorColumn;
import org.metaworks.annotation.Face;
import org.metaworks.annotation.Hidden;
import org.metaworks.annotation.Name;
import org.metaworks.annotation.Order;

import javax.persistence.*;
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

/**
 * Created by uengine on 2017. 5. 29..
 */
@Entity
@Table(name = "TB_PROD")
@Multitenant
@TenantDiscriminatorColumn(name = "TENANTID", contextProperty = "tenant-id")
@Face(displayName = "제품")
public class Product implements BeforeSave, AfterLoad {

    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    Long pNo;
    @Hidden
    @org.metaworks.annotation.Id
        public Long getpNo() {
            return pNo;
        }
        public void setpNo(Long pNo) {
            this.pNo = pNo;
        }


    String prodNumber;
    private boolean deleted;

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

    String prodStandard;
    @Face(displayName = "대표규격")
    @Order(30)
        public String getProdStandard() {
            return prodStandard;
        }
        public void setProdStandard(String prodStandard) {
            this.prodStandard = prodStandard;
        }

    String prodStandard2;
    @Face(displayName = "규격2")
    @Order(40)
        public String getProdStandard2() {
            return prodStandard2;
        }
        public void setProdStandard2(String prodStandard2) {
            this.prodStandard2 = prodStandard2;
        }

    String prodStandard3;
    @Face(displayName = "규격3")
    @Order(50)
        public String getProdStandard3() {
            return prodStandard3;
        }
        public void setProdStandard3(String prodStandard3) {
            this.prodStandard3 = prodStandard3;
        }

    String prodStandard4;
    @Face(displayName = "규격4")
    @Order(60)
    @Hidden
        public String getProdStandard4() {
            return prodStandard4;
        }
        public void setProdStandard4(String prodStandard4) {
            this.prodStandard4 = prodStandard4;
        }

    long curRestNum;
    @Face(displayName = "현재재고수")
    @Order(70)
        public long getCurRestNum() {
            return curRestNum;
        }
        public void setCurRestNum(long curRestNum) {
            this.curRestNum = curRestNum;
        }

    long optiNum;
    @Face(displayName = "적정재고수")
    @Order(80)
        public long getOptiNum() {
            return optiNum;
        }
        public void setOptiNum(long optiNum) {
            this.optiNum = optiNum;
        }


    public void setDeleted(boolean deleted) {
        this.deleted = deleted;
    }

    @Hidden
    public boolean isDeleted() {
        return deleted;
    }


    @Column(name="TENANTID", insertable=false, updatable=false)
    String tenantId;
    @Hidden
        public String getTenantId() {
            return tenantId;
        }
        public void setTenantId(String tenantId) {
            this.tenantId = tenantId;
        }

    @OneToMany(cascade = CascadeType.ALL, mappedBy = "product")
    List&lt;Property&gt; props;
        @Hidden
        public List&lt;Property&gt; getProps() {
            return props;
        }
        public void setProps(List&lt;Property&gt; props) {
            this.props = props;
        }


    @Transient
    Map&lt;String, String&gt; props_;
        @JsonAnyGetter
        @Hidden
        public Map&lt;String, String&gt; getProps_() {
            return props_;
        }
        public void setProps_(Map&lt;String, String&gt; props_) {
            this.props_ = props_;
        }
        @JsonAnySetter
        public void addProps_(String key, String value) {
            if(this.props_ == null)
                this.props_ = new HashMap&lt;String, String&gt;();

            this.props_.put(key, value);
        }


    @Override //this will not be required if the CASCADE option operates properly.
    public void beforeSave() {

        if(getProps_()!=null){
            setProps(new ArrayList&lt;Property&gt;());

            for(String key : getProps_().keySet()){
                Property property = new Property();
                property.setProduct(this); ///// this part is specific
                property.setPropName(key);
                property.setValue(getProps_().get(key));

                getProps().add(property);

            }
        }

    }

    @Override
    public void afterLoad() {
        if(getProps()!=null){
            setProps_(new HashMap&lt;String, String&gt;());

            for(Property property : getProps()){
                getProps_().put(property.getPropName(), property.getValue());
            }
        }
    }
}

          </code-block>
        </section>
      </article>

        </section>


        <section>
          <p>레포지토리 선언:</p>
          <code-block lang="java">
package com.moornmo.ltms;

import org.springframework.data.jpa.repository.Query;
import org.springframework.data.repository.PagingAndSortingRepository;
import org.springframework.data.repository.query.Param;
import org.springframework.data.rest.core.annotation.RepositoryRestResource;

import java.util.List;

@RepositoryRestResource(collectionResourceRel = "product", path = "product")
public interface ProductRepository extends MetaworksRepository&lt;Product, Long&gt; {
}


          </code-block>
        </section>

    </div>
  </page-content>
</template>

<style lang="sass" scoped>
  .main-content {
    position: relative;
  }

  article {
    max-width: 960px;
  }

  section + section,
  article + article {
    margin-top: 36px;
  }

  .code-block,
  .md-tabs {
    max-width: 100%;
  }

  .md-tab {
    border-top: 1px solid rgba(#000, .12);
    padding: 0;
  }

  iframe {
    height: auto;
    min-height: 620px;
  }
</style>
