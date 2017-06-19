<template>
  <page-content page-title="About">
    <div class="main-content">
      <section>
        <h2 class="md-headline">Author</h2>
        <div class="author-card">
        <md-avatar class="md-large">
                      <img src="https://avatars0.githubusercontent.com/u/487999?v=3&s=460" alt="Rick Jang">
                    </md-avatar>
          <div class="author-card-info">


            <span>Rick Jang from uEngine Solutions & Open Cloud Engine</span>
            <div class="author-card-links">
              <a href="https://https://avatars0.githubusercontent.com/u/487999?v=3&s=460" target="_blank" rel="noopener">Open cloud engine</a>
              <a href="https://www.uengine.org" target="_blank" rel="noopener">uEngine website</a>
              <a href="https://www.opence.org" target="_blank" rel="noopener">Open cloud engine</a>
            </div>
          </div>
        </div>
      </section>

      <section>
        <h2 class="md-headline">Browser Support</h2>

        <p>Metaworks4, Vue Material, and Vue2 supports the latest version of all Browsers. This means:</p>
        <ul>
          <li>Google Chrome 52+</li>
          <li>Firefox 48+ </li>
          <li>Safari 9+ </li>
          <li>Opera 38+ </li>
          <li>Edge 12+ </li>
          <li>IE 11</li>
        </ul>
      </section>

      <section>
        <h2 class="md-headline">Credits and Thanks</h2>
        <ul>
          <li>Thanks a lot to <a href="https://github.com/marcosmoura" target="_blank">Marcos Moura</a> Vue Material library</li>
        </ul>
      </section>

      <section>
        <h2 class="md-headline">Internal Dependencies</h2>
        You don't need to include any other library to work with vue-material. The focus of this project is to have a standalone build with no external dependence, but aiming to deliver the best experience without break the compatibility with the Vue.js core.
        <ul>
          <li>
            <a href="https://spring.io/guides/gs/accessing-data-jpa/" rel="noopener" target="_blank">Spring Data JPA</a>
          </li>
          <li>
            <a href="https://spring.io/guides/gs/accessing-data-rest/" rel="noopener" target="_blank">Spring Hateoas REST</a>
          </li>
          <li>
            <a href="https://github.com/TheOpenCloudEngine/metaworks" rel="noopener" target="_blank">Metaworks 3 & 2</a>
          </li>


          <li>
            <a href="https://vuematerial.github.io/#/getting-started" rel="noopener" target="_blank">Vue Material</a>
          </li>
          <li>
            <a href="http://vuejs.org" rel="noopener" target="_blank">Vue JS</a>
          </li>
        </ul>
      </section>

      <section>
        <h2 class="md-headline">License</h2>
        <p>MIT</p>
      </section>
    </div>
  </page-content>
</template>

<style lang="sass" scoped>
  section {
    max-width: 960px;

    + section {
      margin-top: 56px;
    }
  }

  .author-card {
    display: flex;
    align-items: center;

    .md-avatar {
      margin-right: 16px;
    }

    .author-card-info {
      display: flex;
      flex-flow: column;
      flex: 1;
    }

    span {
      font-size: 16px;
    }

    .author-card-links {
      display: flex;

      a + a {
        margin-left: 8px;
      }
    }
  }
</style>
