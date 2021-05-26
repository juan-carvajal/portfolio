<template>
  <q-page class="flex flex-center page-bg">
    <!-- <img alt="Quasar logo" src="~assets/quasar-logo-full.svg" />

    <q-card class="my-card blurred-box">
      <q-item>
        <q-item-section avatar>
          <q-avatar>
            <img src="https://cdn.quasar.dev/img/avatar2.jpg" />
          </q-avatar>
        </q-item-section>

        <q-item-section>
          <q-item-label>Title</q-item-label>
          <q-item-label caption>Subhead</q-item-label>
        </q-item-section>
      </q-item>

      <img src="https://cdn.quasar.dev/img/parallax2.jpg" />
    </q-card>

    <div class="my-card blurred-box">hell</div> -->

    <div style="z-index:1;">
      <h1>Hello!</h1>

      <q-card class="my-card blurred-box">
        <q-item>
          <q-item-section avatar>
            <q-avatar>
              <img src="https://cdn.quasar.dev/img/avatar2.jpg" />
            </q-avatar>
          </q-item-section>

          <q-item-section>
            <q-item-label>Title</q-item-label>
            <q-item-label caption>Subhead</q-item-label>
          </q-item-section>
        </q-item>

        <img src="https://cdn.quasar.dev/img/parallax2.jpg" />
      </q-card>

      <q-card class="my-card blurred-box">
        <q-item>
          <q-item-section avatar>
            <q-avatar>
              <img src="https://cdn.quasar.dev/img/avatar2.jpg" />
            </q-avatar>
          </q-item-section>

          <q-item-section>
            <q-item-label>Title</q-item-label>
            <q-item-label caption>Subhead</q-item-label>
          </q-item-section>
        </q-item>

        <img src="https://cdn.quasar.dev/img/parallax2.jpg" />
      </q-card>
      <p v-for="i in 100" :key="i">
        Lorem ipsum dolor
      </p>

      <q-card class="my-card blurred-box">
        <q-item>
          <q-item-section avatar>
            <q-avatar>
              <img src="https://cdn.quasar.dev/img/avatar2.jpg" />
            </q-avatar>
          </q-item-section>

          <q-item-section>
            <q-item-label>Title</q-item-label>
            <q-item-label caption>Subhead</q-item-label>
          </q-item-section>
        </q-item>

        <img src="https://cdn.quasar.dev/img/parallax2.jpg" />
      </q-card>
    </div>

    <!-- <div class="night">
      
    </div> -->

    <div class="night">
      <div
        class="shooting_star"
        style="z-index:0"
        v-for="i in 25"
        :key="i"
      ></div>
    </div>
  </q-page>
</template>

<script>
export default {
  name: "PageIndex"
};
</script>
<style lang="scss">
body {
  overflow-x: hidden;
}

$shooting-time: 3000ms;

.night {
  position: absolute;
  width: 100%;
  height: 100%;
  //transform: rotateZ(90deg);
  //animation: sky 200000ms linear infinite;
}

.shooting_star {
  position: absolute;
  left: 1%;
  top: 1%;
  // width: 100px;
  height: 2px;
  background: linear-gradient(
    -45deg,
    rgba(95, 145, 255, 1),
    rgba(0, 0, 255, 0)
  );
  border-radius: 999px;
  filter: drop-shadow(0 0 6px rgba(105, 155, 255, 1));
  animation: tail $shooting-time ease-in-out infinite,
    shooting $shooting-time ease-in-out infinite;

  &::before {
    content: "";
    position: absolute;
    top: calc(50% - 1px);
    right: 0;
    // width: 30px;
    height: 2px;
    background: linear-gradient(
      -45deg,
      rgba(0, 0, 255, 0),
      rgba(95, 145, 255, 1),
      rgba(0, 0, 255, 0)
    );
    transform: translateX(50%) rotateZ(45deg);
    border-radius: 100%;
    animation: shining $shooting-time ease-in-out infinite;
  }

  &::after {
    // CodePen Error
    // @extend .shooting_star::before;

    content: "";
    position: absolute;
    top: calc(50% - 1px);
    right: 0;
    // width: 30px;
    height: 2px;
    background: linear-gradient(
      -45deg,
      rgba(0, 0, 255, 0),
      rgba(95, 145, 255, 1),
      rgba(0, 0, 255, 0)
    );
    transform: translateX(50%) rotateZ(45deg);
    border-radius: 100%;
    animation: shining $shooting-time ease-in-out infinite;
    transform: translateX(50%) rotateZ(-45deg);
  }

  @for $i from 1 through 100 {
    &:nth-child(#{$i}) {
      $delay: random(9999) + 0ms;
      top: calc(#{random(1000) / 1000 * 100%} - 100px);
      left: calc(1% - #{random(300) + 0px});
      animation-delay: $delay;
      opacity: random(50) / 100 + 0.5;

      &::before,
      &::after {
        animation-delay: $delay;
      }
    }
  }
}

@keyframes tail {
  0% {
    width: 0;
  }

  30% {
    width: 100px;
  }

  100% {
    width: 0;
  }
}

@keyframes shining {
  0% {
    width: 0;
  }

  50% {
    width: 30px;
  }

  100% {
    width: 0;
  }
}

@keyframes shooting {
  0% {
    transform: translateX(0);
  }

  100% {
    transform: translateX(100vw);
  }
}

@keyframes sky {
  0% {
    transform: rotate(45deg);
  }

  100% {
    transform: rotate(45 + 360deg);
  }
}

.blurred-box {
  box-shadow: 0 0 1rem 0 rgba(0, 0, 0, 0.2);
  border-radius: 5px;
  background-color: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(5px);
}

.my-card {
  width: 100%;
  max-width: 250px;
}

.page-bg {
  /* background: url(https://images.unsplash.com/photo-1544306094-e2dcf9479da3) no-repeat;
  background-size: cover; */
  background: radial-gradient(ellipse at bottom, $primary 0%, $dark 100%);
}
</style>
