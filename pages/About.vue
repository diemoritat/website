<template>
  <v-layout class="vv-container">
    <v-container class="indexed">
      <v-flex xs-12 text-xs-center>
        <img class="vv-logo" src="~/assets/images/logo.png" alt="VueVixens logo">
      </v-flex>
      <v-flex xs12 v-if="!!story.content">
        <template v-for="element in story.content.body">
          <h2 class="vv-subheading font-lato text-xs-center" :key="element.title">
            {{ element.title }}
          </h2>
          <div class="about-content" v-html="toHtml(element.content)" :key="element.title"></div>
        </template>
      </v-flex>
    </v-container>
  </v-layout>
</template>

<script>
import messages from '../assets/translations/about';
import storyblok from '../mixins/storyblok';
import { markdown } from 'markdown';
export default {
  mixins: [storyblok],
  i18n: {
    messages,
  },
  methods: {
    toHtml(text) {
      return markdown.toHTML(text);
    },
  },
};
</script>

<style scoped lang="scss">
.vv-logo {
  width: 100%;
  max-width: 250px;
  margin-bottom: 20px;
}

.about-content {
  padding: 10px 0;
}
</style>
