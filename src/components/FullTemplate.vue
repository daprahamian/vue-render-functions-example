<<template>
  <div>
    <b-alert v-if="options.alert" show>
      <b-link v-if="options.link" :href="options.link">
        <slot></slot>
        <b-badge v-if="options.badge">{{options.badge}}</b-badge>
      </b-link>
      <span v-else>
        <slot></slot>
        <b-badge v-if="options.badge">{{options.badge}}</b-badge>
      </span>
    </b-alert>
    <div v-else>
      <b-link v-if="options.link" :href="options.link">
        <slot></slot>
        <b-badge v-if="options.badge">{{options.badge}}</b-badge>
      </b-link>
      <span v-else>
        <slot></slot>
        <b-badge v-if="options.badge">{{options.badge}}</b-badge>
      </span>
    </div>
  </div>
</template>

<<script>
export default {
  name: 'full-template',
  props: ['options'],
};
</script>
