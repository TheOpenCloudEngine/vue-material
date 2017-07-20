<template>
  <page-content page-title="Getting Started">
    <div class="main-content">
      <article>


      The full source code could be found at <a href="https://github.com/jinyoung/sw-modeling-example">https://github.com/jinyoung/sw-modeling-example</a>
        <section>
          <h2 class="md-headline">The 1-2-3 of mw4</h2>



        <section>
          <p>1. Declare the Domain Class:</p>
          <code-block lang="java" v-html>
package com.autoinsurance;

import org.eclipse.persistence.annotations.Multitenant;
import org.eclipse.persistence.annotations.TenantDiscriminatorColumn;
import org.metaworks.annotation.*;
import org.metaworks.multitenancy.persistence.TenantProperties;

import javax.persistence.*;
import javax.persistence.Id;
import javax.persistence.Table;
import java.io.Serializable;

@Entity
@org.hibernate.annotations.Proxy(lazy=false)
@Table(name="Customer")
@Multitenant
@TenantDiscriminatorColumn(
    name = "TENANTID",
    contextProperty = "tenant-id"
)
public class Customer implements Serializable{
  public Customer() {
  }
  
  @Column(name="Id", nullable=false, length=19) 
  @Id 
  @GeneratedValue(generator="COM_AUTOINSURANCE_CUSTOMER_ID_GENERATOR")  
  @org.hibernate.annotations.GenericGenerator(name="COM_AUTOINSURANCE_CUSTOMER_ID_GENERATOR", strategy="native")  
  private Long id;
  
  @Column(name="FirstName", nullable=true, length=255)
  private String firstName;
  
  @Column(name="LastName", nullable=true, length=255)
  private String lastName;
  
  @Column(name="Address", nullable=true, length=255)
  private String address;

  @Column(name="Age", nullable=false, length=10)
  private int age;

  @Column(name="BirthDay", nullable=true)
  @Temporal(TemporalType.DATE)
  private java.util.Date birthDay;

  @OneToMany(mappedBy="customer", targetEntity=com.autoinsurance.Vehicle.class)
  @org.hibernate.annotations.Cascade({org.hibernate.annotations.CascadeType.SAVE_UPDATE, org.hibernate.annotations.CascadeType.LOCK})
  @org.hibernate.annotations.LazyCollection(org.hibernate.annotations.LazyCollectionOption.TRUE)
  private java.util.Set vehicles = new java.util.HashSet();

  private void setId(long value) {
    setId(new Long(value));
  }

  public void setId(Long value) {
    this.id = value;
  }

  @org.metaworks.annotation.Id
  @Hidden
  public Long getId() {
    return id;
  }

  public Long getORMID() {
    return getId();
  }

  public void setFirstName(String value) {
    this.firstName = value;
  }

  @Order(1)
  @Group(name="Default Information")
  public String getFirstName() {
    return firstName;
  }

  public void setLastName(String value) {
    this.lastName = value;
  }

  @Order(2)
  @Group(name="Default Information")
  public String getLastName() {
    return lastName;
  }

  public void setAddress(String value) {
    this.address = value;
  }

  @Order(3)
  @Face(displayName = "주소")
  @Group(name="Default Information")
  public String getAddress() {
    return address;
  }

  public void setAge(int value) {
    this.age = value;
  }

  @Order(4)
  @Face(displayName = "나이")
  @Group(name="Bio Information")
  public int getAge() {
    return age;
  }

  public void setBirthDay(java.util.Date value) {
    this.birthDay = value;
  }

  @Order(5)
  @Face(displayName = "생년월일")
  @Group(name="Bio Information")
  public java.util.Date getBirthDay() {
    return birthDay;
  }

  @Hidden
  public void setVehicles(java.util.Set value) {
    this.vehicles = value;
  }

  public java.util.Set getVehicles() {
    return vehicles;
  }

  public String toString() {
    return String.valueOf(getId());
  }

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


}


          </code-block>
        </section>



          <section>
            <p>2. Declare the Repository:</p>
            <code-block lang="java">

package com.autoinsurance;

import org.metaworks.multitenancy.persistence.MultitenantRepository;
import org.springframework.data.repository.PagingAndSortingRepository;
import org.springframework.data.rest.core.annotation.RepositoryRestResource;

/**
 * Created by uengine on 2017. 7. 3..
 */
@RepositoryRestResource(collectionResourceRel = &quot;customer&quot;, path=&quot;customer&quot;)
public interface CustomerRepository extends MultitenantRepository&lt;Customer, Long&gt; {
}


            </code-block>
          </section>


          <section>
          <p>3. Write HTML-like page and bind it to the Domain Class: </p>
 <code-block lang="html">
 
&lt;!DOCTYPE html&gt;
&lt;html lang=&quot;en&quot;&gt;
&lt;head&gt;
    &lt;meta charset=&quot;UTF-8&quot;&gt;
    &lt;title&gt;Title&lt;/title&gt;


    &lt;script src=&quot;https://unpkg.com/vue&quot;&gt;&lt;/script&gt;
    &lt;script src=&quot;https://unpkg.com/vue-material@0.7.1&quot;&gt;&lt;/script&gt;
    &lt;script src=&quot;https://cdnjs.cloudflare.com/ajax/libs/require.js/2.3.3/require.js&quot;&gt;&lt;/script&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;https://unpkg.com/vue-material@0.7.1/dist/vue-material.css&quot;&gt;
    &lt;link href=&quot;https://fonts.googleapis.com/icon?family=Material+Icons&quot; rel=&quot;stylesheet&quot;&gt;



&lt;/head&gt;
&lt;body&gt;

&lt;script&gt;

    Vue.use(VueMaterial)

&lt;/script&gt;


&lt;script src=&quot;http://rawgit.com/TheOpenCloudEngine/metaworks4/master/src/main/resources/static/object-grid.js&quot;&gt;&lt;/script&gt;
&lt;script src=&quot;http://rawgit.com/TheOpenCloudEngine/metaworks4/master/src/main/resources/static/object-form.js&quot;&gt;&lt;/script&gt;
&lt;script src=&quot;http://rawgit.com/TheOpenCloudEngine/metaworks4/master/src/main/resources/static/service-locator.js&quot;&gt;&lt;/script&gt;
&lt;script src=&quot;http://rawgit.com/TheOpenCloudEngine/metaworks4/master/src/main/resources/static/class-selector.js&quot;&gt;&lt;/script&gt;

&lt;script src=&quot;http://rawgit.com/TheOpenCloudEngine/metaworks4/master/src/main/resources/static/iam-client/jqeury.js&quot; charset=&quot;utf-8&quot;&gt;&lt;/script&gt;
&lt;script src=&quot;http://rawgit.com/TheOpenCloudEngine/metaworks4/master/src/main/resources/static/iam-client/iam-client.js&quot; charset=&quot;utf-8&quot;&gt;&lt;/script&gt;
&lt;script src=&quot;http://rawgit.com/TheOpenCloudEngine/metaworks4/master/src/main/resources/static/iam-login.js&quot;&gt;&lt;/script&gt;

&lt;script src=&quot;ssp-class.js&quot;&gt;&lt;/script&gt;

&lt;div id=&quot;app&quot;&gt;

    &lt;iam-login iam-server=&quot;http://iam.uengine.io:8080&quot; ref=&quot;login&quot; :listener=&quot;$root&quot; v-if=&quot;!loggedIn&quot;&gt;&lt;/iam-login&gt;

    &lt;service-locator host=&quot;http://localhost:8080&quot; ref=&quot;backend&quot;&gt;&lt;/service-locator&gt;

    &lt;md-tabs id=&quot;tab&quot; @change=&quot;tabChanged&quot; v-if=&quot;loggedIn&quot;&gt;
        &lt;md-tab id=&quot;customers&quot; md-label=&quot;Customers&quot;&gt;

            &lt;object-grid ref=&quot;grid&quot;
                     java=&quot;com.autoinsurance.Customer&quot;
                     :filter-key=&quot;searchQuery&quot;
                     :column-changer=&quot;columnChanger&quot;
                     :online = &quot;true&quot;
                     :data = &quot;[]&quot;
                     :options=&quot;{pagination: true, toolbar: true}&quot;
                     service-locator = &quot;backend&quot;
                     v-if=&quot;loggedIn&quot;
            &gt;
            &lt;/object-grid&gt;
        &lt;/md-tab&gt;
        &lt;md-tab id=&quot;ssp-customer&quot; md-label=&quot;Selfservice - Class management&quot;&gt;
            &lt;ssp-class
                java=&quot;com.autoinsurance.Customer&quot;
                service-locator=&quot;backend&quot;&gt;
            &lt;/ssp-class&gt;
        &lt;/md-tab&gt;
    &lt;/md-tabs&gt;

&lt;/div&gt;

&lt;script&gt;

    var app = new Vue({
        el: &apos;#app&apos;,
        props: {loggedIn: Boolean},

        methods: {

            onLoggedIn: function(){
                this.loggedIn = true;
            },


        }

    })


&lt;/script&gt;






&lt;/body&gt;
&lt;/html&gt;

   </code-block>
          </section>
        </section>
      </article>
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
