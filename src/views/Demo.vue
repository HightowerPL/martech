<template>
  <div id="app">

    <Header></Header>

    <section class="screen">
      <div class="container">
        <img
          class="screen__img--momentum"
          :src="require('../assets/' + screen.img + '.svg')"
          :alt="screen.img"
        />
        <h2 class="screen__text screen__text--heading">{{screen.heading}}</h2>
        <p class="screen__text screen__text--sub">{{ screen.sub }}</p>

      </div>
    </section>

    <transition name="slide-fade">
      <Card v-show="openCard" @close="closeCard"></Card>
    </transition>

    <section class="lower">
      <div class="container">
        <ul class="lower__list">
          <li class="lower__list-item" v-for="(item, index) in list" :key="index">
            <img
              class="lower__img--svg"
              :src="require('../assets/' + item[0] + '.svg')"
              :alt="item[0]"
            />
            <span class="lower__text">{{ item[1] }}</span>
          </li>
        </ul>
      </div>
    </section>

    <transition name="slide-fade-down">
      <div class="request-wrap" v-show="showRequestBtn">
        <button
          class="request-wrap__btn btn btn--primary"
          @click="openCard = true">
          <span>
          Request a Demo
          </span>
        </button>
      </div>
    </transition>

    <Footer></Footer>

  </div>
</template>

<script>
import Header from '../components/Header.vue';
import Card from '../components/Card.vue';
import Footer from '../components/Footer.vue';

export default {
  name: 'About',
  components: {
    Header,
    Card,
    Footer,
  },
  data() {
    return {
      screen: {
        img: 'momentum-logo',
        heading: 'Asset Creation Made Easy For The Enterprise',
        sub:
          'Enabling anyone to build on brand emails and landing pages in minutes.',
      },
      list: [
        ['circle', 'Easly integrate momentum into workflow'],
        ['star', 'Quickly build brand emails'],
        ['arrow', 'Review and approve teams emails and pages'],
      ],
      openCard: false,
      showRequestBtn: false,
    };
  },
  created() {
    window.addEventListener('resize', this.resizeHandler);
    this.openCard = window.outerWidth > 1240;
  },
  destroyed() {
    window.removeEventListener('resize', this.resizeHandler);
  },
  methods: {
    closeCard() {
      this.openCard = false;
    },
    resizeHandler() {
      if (window.outerWidth > 1240) {
        this.openCard = true;
        this.showRequestBtn = false;
      } else {
        this.showRequestBtn = true;
      }
    },
  },
};
</script>

<style lang="scss">

.container {
  max-width: 1240px;
  margin: 0 auto;
  padding: 0 2rem;
  position: relative;
}

.screen {
  background: rgba(0,0,0,.1) ;
  background-size: 100% 100%;
  color: var(--white);
  padding: 14rem 4rem;
  font-weight: 700;
  overflow: hidden;
  position: relative;

  &:before {
    content: '';
    width: 100%;
    height: 100%;
    background: url('../assets/momentum-logo-only.svg') 50% 60% no-repeat;
    background-size: contain;
    position: absolute;
    top: -15rem;
    left: 10rem;
    z-index: 0;
    opacity: 0.2;
    transform: scale(3.5);
  }

  &__img {
    &--momentum {
      max-width: 24rem;
      margin-bottom: 4rem;
    }
  }

  &__text {
    font-weight: 700;
    max-width: 52rem;

    &--heading {
      font-size: 4.6rem;
      margin: 0 auto 2rem;
    }

    &--sub {
      margin: 0 auto;
      font-size: 2.4rem;

    }
  }
}

.lower {
  background-color: var(--darkSlate);
  height: 100%;
  position: relative;
  padding: 6rem 0 ;
  text-align: left;

  &:before {
    content: '';
    background: url('../assets/arrow-gray.svg') center center no-repeat;
    background-size: contain;
    z-index:-1;
    transform: rotate(45deg);
    width: 140px;
    height: 235px;
    position: absolute;
    top: 2rem;
    left: 0;
  }

  &__list {
    list-style-type: none;
    padding: 0;
    margin: 0;
    &-item {
      display: flex;
      align-items: center;
      margin-bottom: 3.3rem;
    }
  }

  &__img {
    &--svg {
      max-height: 2.7rem;
      margin-right: 2.2rem;
      color: var(--hotPink);
    }
  }
  &__text {
    font-size: 1.8rem;
    color: white;
  }
}

.btn {
  font-family: 'museo-sans-rounded', sans-serif;
  font-weight: 700;
  border: none;
  height: 4.8rem;
  font-size: 2rem;
  cursor: pointer;

  &--primary {
    background-color: var(--hotPink);
    border: 2px solid var(--hotPink);
    color: var(--white);
    border-radius: 5px;
    font-weight: 700;
      line-height: 4rem;

    padding: 0 2.4rem;
    position: relative;
    overflow: hidden;
    transition: color .4s;

    > * {
      position: relative;
      z-index: 2;
    }

    &::before {
      content: '';
      width: .2rem;
      background-color: var(--white);
      position: absolute;
      top: 0;
      bottom:0;
      left: -1rem;
      transition: transform .8s;
      z-index: 1;
    }

    &:hover {
      color: var(--hotPink);

      &::before {
        transform: scaleX(500);

      }
    }
  }
}

.request-wrap {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    z-index: 90;
    padding: 2rem;
    &__btn {
      max-width: 440px;
      width: 100%;
      box-shadow: 0 0 20px rgba(0,0,0,.35);
    }
}

@media screen and (min-width: 920px) {
  .screen {
    padding-top: 17.5rem;
    text-align: left;
    &:before {
      content: '';
      top: 9rem;
      left: 32rem;
      transform: scale(1.25);
    }
    &__text {
        &--heading, &--sub {
          margin-left: 0;
          margin-right: 0;
        }
    }
  }
  .lower {
    padding-bottom: 24rem;
    &__list {
      list-style-type: none;
      padding: 0;
      margin: 0;
      &-item {
        display: flex;
        align-items: center;
        justify-content: flex-start;
      }
    }
  }
}

.slide-fade-enter-active {
  transition: all .6s ease;
}

.slide-fade-leave-active {
  transition: all .6s ease;
}

.slide-fade-enter, .slide-fade-leave-to {
  transform: translateX(-20px);
  opacity: 0;
}

//Slide down fade
.slide-fade-down-enter-active {
  transition: all .6s ease;
}

.slide-fade-down-leave-active {
  transition: all .6s ease;
}

.slide-fade-down-enter, .slide-fade-down-leave-to {
  transform: translateY(20px);
  opacity: 0;
}

.md-theme-default a:not(.md-button) {
  color: inherit;
}

</style>
