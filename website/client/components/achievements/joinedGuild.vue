<template lang="eng">
  b-modal#joined-guild(:title="$t('modalAchievement')", size='lg', :hide-footer="true")
    .modal-body.text-center
      // @TODO: +achievementAvatar('guild',0)
      achievement-avatar.avatar
      p {{ $t('joinedGuildText') }}
      br
      button.btn.btn-primary(@click='close()') {{ $t('huzzah') }}
    achievement-footer
</template>

//I think it will look better this way
<style scoped>
  .avatar {
    margin-left: 10em;
    margin-bottom: 2em;
    margin-top: 2em;
  }
</style>

<script>
import bModal from 'bootstrap-vue/lib/components/modal';
import achievementFooter from './achievementFooter';
import achievementAvatar from './achievementAvatar';

export default {
  components: {
    bModal,
    achievementFooter,
    achievementAvatar,
  },
  methods: {
    close () {
      this.$root.$emit('hide::modal', 'joined-guild');
    },
  },
};
</script>
