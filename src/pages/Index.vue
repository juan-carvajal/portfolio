<template>
  <q-page class="flex flex-center bg-primary">
    <div class="nightv2 flex flex-center">
      <div
        class="shooting_star"
        style="z-index:0"
        v-for="i in 25"
        :key="i"
      ></div>

      <div class="docpage q-px-lg" style="z-index:1;">
        <div class="text-center glow">
          <h2 class="text-bold">Hello!</h2>
          <p class="text-h4">My name is Juan Carvajal, Welcome!</p>
          <div class="text-center">
            <p class="text-subtitle2 q-my-sm">
              <span class="text-bold">Software Engineer (Fullstack)</span
              ><q-icon class="q-ml-sm" name="fas fa-rocket"></q-icon>
            </p>

            <q-separator inset></q-separator>
            <p class="text-subtitle2 q-my-sm">
              <span class="text-bold">Software Architect</span
              ><q-icon class="q-ml-sm" name="fas fa-drafting-compass"></q-icon>
            </p>
            <q-separator inset></q-separator>
            <p class="text-subtitle2 q-my-sm">
              <span class="text-bold">Researcher</span
              ><q-icon class="q-ml-sm" name="fas fa-flask"></q-icon>
            </p>
          </div>

          <p class="text-body1 text-weight-light">
            I am an avid problem solver, a fast and self-taught learner who is
            always looking for an opportunity to better myself. My main interest
            is to be at the forefront of the ongoing industrial revolution that
            is going to transform traditional manufacturing, services and TI
            industries, using modern and avant-garde technologies. I also have
            interest in modern topics such as automation, data science, machine
            learning and agile development, among others.
          </p>
        </div>
      </div>
    </div>

    <div>
      <p class="text-caption" v-for="i in 25" :key="i">
        Lorem Ipsum
      </p>
    </div>

    <!-- <div>
      <div class="docpage" style="z-index:1;">
        <div class="text-center glow">
          <h2 class="text-bold">Hello!</h2>
          <p class="text-h4">My name is Juan Carvajal, Welcome!</p>
          <div class="text-center">
            <p class="text-subtitle2 q-my-sm">
              <span class="text-bold">Software Engineer (Fullstack)</span
              ><q-icon class="q-ml-sm" name="fas fa-rocket"></q-icon>
            </p>

            <q-separator inset></q-separator>
            <p class="text-subtitle2 q-my-sm">
              <span class="text-bold">Software Architect</span
              ><q-icon class="q-ml-sm" name="fas fa-drafting-compass"></q-icon>
            </p>
            <q-separator inset></q-separator>
            <p class="text-subtitle2 q-my-sm">
              <span class="text-bold">Researcher</span
              ><q-icon class="q-ml-sm" name="fas fa-flask"></q-icon>
            </p>
          </div>

          <p class="text-body1 text-weight-light">
            I am an avid problem solver, a fast and self-taught learner who is
            always looking for an opportunity to better myself. My main interest
            is to be at the forefront of the ongoing industrial revolution that
            is going to transform traditional manufacturing, services and TI
            industries, using modern and avant-garde technologies. I also have
            interest in modern topics such as automation, data science, machine
            learning and agile development, among others.
          </p>
        </div>
      </div>
    </div> -->
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

.nightv2 {
  position: relative;
  width: 100%;
  height: calc(100vh);
  margin-top: -50px;
  background: linear-gradient(0deg, $primary 0%, $dark 100%);
}

.night {
  position: absolute;
  width: 100%;
  height: calc(100% + 50px);
  margin-top: -50px;
  background: linear-gradient(0deg, $primary 0%, $dark 100%);
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
  margin-top: -50px;
}
</style>
