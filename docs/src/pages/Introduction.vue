<template>
  <page-content page-title="Introduction">
    <div class="main-content">
      <div class="introduction">
        <div class="button-actions">
          <div class="example">
            <img src="assets/vue-material-example.png" alt="Model driven & Material Design">
          </div>

          <div class="introduction">메타웍스4 (a.k.a. 메타포어) UI 플랫폼</div>

          <md-button class="md-primary md-raised" href="#/getting-started">시작하기</md-button>
          <md-button class="md-primary md-raised" href="https://github.com/TheOpenCloudEngine/micro-service-architecture-vuejs" target="_blank" rel="noopener">깃허브</md-button>
        </div>

        <div class="row">
          <div class="column">
            <h2 class="md-headline">마이크로 서비스 아키텍처</h2>
            <p>메타웍스4 UI 플랫폼에서 제공하는 컴포넌트들은 클라우드 기반의 특히 SaaS 애플리케이션을 개발함에 필요한 아키텍처가 이미 적용되어 있습니다.
            클라이언트 중심의 매시업을 위한 IAM 토큰 기반 인증, 멀티테넌시를 위한 객체 정보 기반 그리드와 폼, 셀프서비스를 위한 포탈과 매시업 도구들을 제공하는 수준 높은 애플리케이션을 개발하세요.</p>
          </div>

          <div class="column">
            <h2 class="md-headline">도메인 (모델) 주도 개발</h2>
            <p>메타웍스4는 Spring Hateoas와 JPA, 그리고 기존 메타웍스2,3의 메타데이터 중심 아키텍처를 계승하여 POJO 형식의 도메인 클래스에 어노테이션을 추가하는 것 만으로 복잡한 기업용 데이터베이스 애플리케이션을 매우 높은 생산성으로 개발할 수 있습니다.
            향후 비교할 수 없는 유지보수 편의성과 유연성을 보장하는 DDD (도메인 주도 설계)와 MDD (모델 중심 개발) 방식을 경험하세요.</p>
          </div>

          <div class="column">
            <h2 class="md-headline">머터리얼 디자인 & Vue 2</h2>
            <p>메타웍스4는 구글의 머터리얼 디자인 가이드라인을 준수합니다 - <a href="http://material.google.com" target="_blank" rel="noopener">Material Design</a>. 모든 스크린에 최적화된 예쁜 사용자 경험을 여러분의 애플리케이션에 적용하세요.</p>
          </div>

        </div>
      </div>
    </div>
  </page-content>
</template>

<style lang="sass" scoped>
  .introduction {
    max-width: 960px;
    margin: 0 auto;
  }

  .example {
    margin-bottom: 24px;
    overflow: hidden;

    img {
      margin: -45px auto;
      display: block;
    }
  }

  .button-actions {
    margin-bottom: 16px;
    text-align: center;

    .introduction {
      margin-bottom: .8em;
      font-size: 20px;
      line-height: 1.6em;
    }

    .md-button {
      margin-left: 0;
      color: #fff !important;
    }
  }

  .row {
    margin: 0 -10px;
    display: flex;
    flex-flow: row wrap;
  }

  .column {
    margin: 0 10px;
    flex: 1 1 30%;

    @media (max-width: 640px) {
      flex: 1 1 100%;
    }
  }
</style>
