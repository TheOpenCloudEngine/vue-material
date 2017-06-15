<template>
  <page-content page-title="Getting Started">
    <div class="main-content">
      <article>
        <section>
          <h2 class="md-headline">Include Fonts and Icons</h2>

          <p>Use Roboto and Google Icons from Google CDN:</p>
          <code-block lang="xml">
            &lt;link rel=&quot;stylesheet&quot; href=&quot;//fonts.googleapis.com/css?family=Roboto:300,400,500,700,400italic&quot;&gt;
            &lt;link rel=&quot;stylesheet&quot; href=&quot;//fonts.googleapis.com/icon?family=Material+Icons&quot;&gt;
          </code-block>
        </section>
      </article>

      <article>
        <h2 class="md-headline">Usage</h2>

        <section>
          <p>Import and use the whole library:</p>
          <code-block lang="xml">

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


&lt;/script&gt;
          </code-block>
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
