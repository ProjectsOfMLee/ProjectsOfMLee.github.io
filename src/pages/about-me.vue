<template>
  <div class="container">
    <aside>
      <HeroAvatar>
        <img
          src="@/assets/img/profile.jpg"
          alt="me"
          width="140"
          loading="lazy"
        />
      </HeroAvatar>
      <BinaryTextSVG />
    </aside>
    <main id="main-content">
      <article class="about-content">
        <h1 class="about-content__headline">About me</h1>
        <p>👋 Hi there! How are you?</p>
        <p>
          I'm Mingyi, a
          <strong>software engineer</strong> dedicated to
          <em> "combining" </em> backend development and artificial intelligence.
        </p>
        <p>
          Since I was 12, I have been coding with passion and joy. 
          As I majored in Statistics and Data Science for undergraduate studies, 
          I was intrigued by the power of statistical and Machine Learning models in real-world problem-solving.
          After I accumulated various data science/machine learning engineer internships, 
          I am currently pursuing a MSc degree in Applied Computing at the Deparment of Computer Science at University of Toronto.
        </p>
        <p>
          My go-to programming languages are Python and Java. I am also in my comfort zone working with SQL and its dialects.
          I am a quick learner of algorithms, frameworks and dev tools.
        </p>
        <p>
          Outside of IT, I enjoy listening to (and sometimes writing my own) music. I love musicals, movies and TV series.
          When I was young, I was lucky to have learnt how to sing, play the flute and the guitar, play chess and do ballet dancing.
        </p>
        
      </article>
    </main>
  </div>
</template>

<script setup>
import { useRoute } from 'vue-router'
import config from '../config/siteconfig.json'

const title = 'More About Mingyi Li'
const { description } = config
const route = useRoute()

useHead({
  title,
  meta: [
    {
      name: 'description',
      content: description,
    },
    { property: 'og:type', content: 'website' },
    { property: 'og:title', content: title },
    { property: 'og:description', content: description },
    { property: 'og:url', content: `${config.siteUrl}${route.path}` },
    {
      property: 'twitter:title',
      content: title,
    },
    {
      property: 'twitter:description',
      content: description,
    },
  ],
})
</script>

<route lang="yaml">
meta:
  layout: default
</route>

<style lang="css" scoped>
:global(#app) {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.container {
  flex-flow: row wrap;
  padding: 3rem 0;
}

main {
  padding: 1.2rem 2.4rem;
}

.about-content {
  .about-content__headline {
    font-size: var(--text-2xl);
  }

  p {
    font-size: var(--text-lg);
    opacity: 0.8;
    max-width: 71ch;
  }
}

.binary-text-svg {
  font-family: var(--font-mono);
  font-size: var(--text-xl);
  position: absolute;
  left: 282px;
  top: 387px;
  opacity: 0.3;

  & :deep(tspan) {
    --text-delay: 500ms;

    opacity: 0;
    animation: pulse-spread 3s var(--text-delay) ease-out infinite alternate;

    &:nth-child(1) {
      --text-delay: 500ms;
    }

    &:nth-child(2) {
      --text-delay: 1s;
    }

    &:nth-child(3) {
      --text-delay: 1.5s;
    }

    &:nth-child(4) {
      --text-delay: 2s;
    }

    &:nth-child(5) {
      --text-delay: 2.5s;
    }

    &:nth-child(6) {
      --text-delay: 3s;
    }
  }
}

@keyframes pulse-spread {
  0% {
    opacity: 0;
  }

  100% {
    opacity: 0.3;
  }
}

@media screen and (min-width: 426px) and (max-width: 768px) {
  aside {
    margin-left: 40px;
    padding: 0 2.4rem 0 0;
  }
}

@media screen and (max-width: 425px) {
  aside {
    padding: 0 1rem;
  }

  .container {
    height: 100%;
  }

  .binary-text-svg {
    top: 50%;
    left: 0;
    bottom: 0;
  }
}
</style>
