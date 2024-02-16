<template>
  <div class="skeleton">
    <div class="skeleton__header">
      <div class="skeleton__header-item"></div>
      <div class="skeleton__header-item"></div>
    </div>
    <div class="skeleton__container">
      <section class="skeleton__section">
        <div v-for="(item, index) in skeletonItems" :key="index" :class="item.class"></div>
        <div class="skeleton__btn" v-if="showButton"></div>
      </section>
      <section class="skeleton__section">
        <div class="skeleton__large"></div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      skeletonItems: [
        { class: 'skeleton__medium' },
        { class: 'skeleton__content' },
        { class: 'skeleton__medium' },
        { class: 'skeleton__content' },
        { class: 'skeleton__medium' },
        { class: 'skeleton__content' },
        { class: 'skeleton__medium' },
        { class: 'skeleton__content' }
      ]
    };
  },
  computed: {
    showButton() {
      return window.innerWidth <= 1024;
    }
  }
};
</script>

<style lang="scss" scoped>
$skeleton-background: linear-gradient(90deg, #EEF0F3 24.17%, #F9F9FA 35.95%, #EEF0F3 50%);
$skeleton-border-radius: 8px;

.skeleton {
  width: 100%;
  display: flex;
  flex-direction: column;
  min-height: 100%;

  &__header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 20px;
    border-bottom: 1px solid #b8c1cc;

    &-item {
      width: 100%;
      max-width: 112px;
      height: 24px;
      background: $skeleton-background;
      animation: pulse 1s infinite alternate;
      border-radius: $skeleton-border-radius;
    }
  }

  &__container {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    padding: 32px 20px;

    @media screen and (max-width: 1024px) {
      flex-direction: column;
      justify-content: center;
    }
  }

  &__section {
    @media screen and (max-width: 1024px) {
      &:first-child {
        order: 2;
        .skeleton__medium:nth-child(7),
        .skeleton__content:nth-child(8) {
          display: none;
        }
      }

      &:last-child {
        order: 1;
      }
    }
  }

  &__medium {
    width: 376px;
    height: 24px;
    border-radius: $skeleton-border-radius;
    margin-bottom: 10px;

    @media screen and (max-width: 1024px) {
      width: 100%;
      max-width: 112px;
      height: 24px;

      &:nth-child(4) {
        display: none;
      }
    }
  }

  &__content {
    width: 480px;
    height: 80px;
    border-radius: $skeleton-border-radius;
    margin-bottom: 32px;

    @media screen and (max-width: 1024px) {
      width: 100%;
      max-width: 80px;
    }
  }

  &__btn {
    display: none;

    @media screen and (max-width: 1024px) {
      display: block;
      width: 100%;
      height: 48px;
      border-radius: $skeleton-border-radius;
      margin-top: 150px;
    }
  }

  &__large {
    width: 480px;
    height: 220px;
    border-radius: $skeleton-border-radius;

    @media screen and (max-width: 1024px) {
      width: 100%;
      height: 132px;
      margin-bottom: 16px;
    }
  }

  &__medium,
  &__content,
  &__large,
  &__btn {
    background: $skeleton-background;
    animation: pulse 1s infinite alternate;
  }

  @keyframes pulse {
    0% {
      opacity: 0.5;
    }
    100% {
      opacity: 1;
    }
  }
}
</style>
