<template>
    <div class="claim">
      <h1 class="claim__heading">buy.sell.trade.</h1>
      <div class="claim__content">
        <h3>Community driven</h3>
        <p>We are classified advertisements website with sections devoted to jobs, housing, personals, for sale, items wanted, services, community, gigs, resumes, and discussion forums.</p>
      </div>
      <a class="button button--primary" href="#">learn more</a>
    </div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
  .claim {
    display: flex;
    flex-direction: column;
    justify-content: space-between;

    @media(min-width: 768px) {
      justify-content: unset;
    }

    &__heading {
      font-size: 3.3rem;
      letter-spacing: 2px;

      @media(min-width: 768px) {
        margin: -2rem 0 2rem 0;
        font-size: 6rem;
        letter-spacing: 6px;
        z-index: 1;
      }

      @media(min-width: 1024px) {
        font-size: 7rem;
      }

      @media(min-width: 1200px) {
        letter-spacing: 1.4rem;
        font-size: 9rem;
      }
    }

    &__content {

      @media(min-width: 768px) {
        margin-bottom: 2rem;
      }

      & > h3 {
        font-size: 2rem;

        @media(min-width: 768px) {
          margin-bottom: 1.6rem;
          font-size: 2rem;
          letter-spacing: 3px;
        }

        @media(min-width: 1200px) {
          font-size: 3rem;
        }
      }

      & > p {
        font-size: 1.3rem;
        line-height: 1.5;

        @media(min-width: 1200px) {
          font-size: 2rem;
        }
      }
    }
  }
</style>
