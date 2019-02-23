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

    &__heading {
      font-size: 3.3rem;
      letter-spacing: 2px;
    }

    &__content {

      & > h3 {
        font-size: 2rem;
      }

      & > p {
        font-size: 1.3rem;
        line-height: 1.5;
      }
    }
  }
</style>
