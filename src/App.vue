<template>
  <div id="app">
    <nav
      class="navbar is-fixed-top is-white"
      role="navigation"
      aria-label="dropdown navigation"
    >
      <div class="navbar-brand">
        <div
          class="navbar-item"
        >
          <router-link
            to="/"
            class="logo-text"
            style="margin-right:0.4em; color: #000"
          >
            3D BAG
          </router-link>
          <span
            class="logo-text"
            style="color:#ccc; font-weight:300; margin-right:0.2em"
          >by Heroes</span>
        </div>
      </div>
      <div
        class="navbar-menu"
        :class="{ 'is-active': showBurgerMenu }"
      >
        <div class="navbar-end">
          <LocaleSwitcher />
        </div>
      </div>
    </nav>
    <b-modal
      v-model="showAbout"
      has-modal-card
    >
      <div class="modal-card">
        <header class="modal-card-head">
          <p class="modal-card-title">
            About 3D BAG
          </p>
          <button
            class="delete"
            aria-label="close"
            @click="showAbout = false"
          />
        </header>
        <section class="modal-card-body">
          <div class="content">
            <p>This is a beta release of the renewed version of the 3D BAG service.</p>
            <p>
              Read about <a
                href="https://docs.3dbag.nl/en/"
                target="_blank"
              >who we are and why we created the 3D BAG</a>.
            </p>

            <h2 class="title is-4">
              Copyright and licensing
            </h2>
            <p
              xmlns:cc="http://creativecommons.org/ns#"
              xmlns:dct="http://purl.org/dc/terms/"
            >
              <a
                property="dct:title"
                rel="cc:attributionURL"
                href="https://3dbag.nl"
              >3D BAG</a> by
              <a
                rel="cc:attributionURL dct:creator"
                property="cc:attributionName"
                href="https://3d.bk.tudelft.nl/"
              >3D geoinformation research group</a> is licensed under
              <a
                href="http://creativecommons.org/licenses/by/4.0/?ref=chooser-v1"
                target="_blank"
                rel="license noopener noreferrer"
                style="display:inline-block;"
              >CC BY 4.0<img
                style="height:22px!important;margin-left:3px;vertical-align:text-bottom;"
                src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"
              ><img
                style="height:22px!important;margin-left:3px;vertical-align:text-bottom;"
                src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1"
              ></a>
            </p>
            <p>
              Read the <a
                href="https://docs.3dbag.nl/en/copyright"
                target="_blank"
              >terms of use for the 3D BAG</a>.
            </p>
          </div>
        </section>
      </div>
    </b-modal>
    <router-view
      @show-about="showAbout=true"
    />
  </div>
</template>

<script>

import LocaleSwitcher from './components/LocaleSwitcher';

export default {

	name: 'App',
  	components: {
		LocaleSwitcher,
	},

	data() {

		return {

			showBurgerMenu: false,
			showAbout: false,

		};

	},

	computed: {
		currentLocale() {

			return this.$route.params.locale;

		},
		currentRouteName() {

			return this.$route.name;

		}
	},

};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Barlow&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Inter&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Inter&family=Roboto+Mono&display=swap');


html, body {
  height: 100%;
  width: 100%;
  margin: 0px;
}

#app {

  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100%;
  width: 100%;
  margin: 0;
  padding: 3.25rem 0 0 0;

}

nav.navbar {
  box-shadow: 0 0.5em 1em -0.125em rgb(10 10 10 / 10%), 0 0px 0 1px rgb(10 10 10 / 2%);
}

.logo-text {
  font-family: 'Barlow', sans-serif;
  font-weight: bold;
}

.docs-link {
  background-color: rgb(250 250 250 / 1);
}
</style>
