<template lang="pug">
  b-modal#won-challenge(:title="$t('wonChallenge')", size='md', :hide-footer="true")
    .modal-body.text-center
      h4(v-markdown='user.achievements.challenges[user.achievements.challenges.length - 1]')
      .row
        .col-4
          .achievement-karaoke-2x
        .col-4
          // @TODO: +generatedAvatar({sleep: false})
          avatar(:member='user', :avatar-only='true')
        .col-4
          .achievement-karaoke-2x
      p {{ $t('congratulations') }}
      br
      button.btn.btn-primary(@click='close()') {{ $t('hurray') }}
    .modal-footer
      .col-3
        a.twitter-share-button(href='https://twitter.com/intent/tweet?text=#{tweet}&via=habitica&url=#{env.BASE_URL}/social/won-challenge&count=none') {{ $t('tweet') }}
      .col-4(style='margin-left:.8em')
        .fb-share-button(data-href='#{env.BASE_URL}/social/won-challenge', data-layout='button')
      .col-4(style='margin-left:.8em')
        a.tumblr-share-button(data-href='#{env.BASE_URL}/social/won-challenge', data-notes='none')
</template>

<style scope>
  .achievement-karaoke-2x {
    margin: 0 auto;
    margin-top: 6em;
  }

  .avatar {
    margin-left: 0em;
  }
</style>

<script>
import { mapState } from 'client/libs/store';
import bModal from 'bootstrap-vue/lib/components/modal';
import markdownDirective from 'client/directives/markdown';
import Avatar from '../avatar';

export default {
  components: {
    bModal,
    Avatar,
  },
  directives: {
    markdown: markdownDirective,
  },
  computed: {
    ...mapState({user: 'user.data'}),
  },
  data () {
    let tweet = this.$t('wonChallengeShare');
    return {
      tweet,
    };
  },
  methods: {
    close () {
      this.$root.$emit('hide::modal', 'won-challenge');
    },
  },
};
</script>
