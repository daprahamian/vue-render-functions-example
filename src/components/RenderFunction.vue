<script>
import Alert from 'bootstrap-vue/es/components/alert/alert';
import Badge from 'bootstrap-vue/es/components/badge/badge';
import Link from 'bootstrap-vue/es/components/link/link';

export default {
  name: 'render-function',
  props: ['options'],
  render(h) {
    const { link, badge, alert } = this.options;

    let element = h('span', this.$slots.default);

    if (link) {
      element = h(Link, { props: { href: link } }, [element]);
    }

    if (badge) {
      element = h('div', [
        element,
        h(Badge, badge),
      ]);
    }

    if (alert) {
      element = h(
        Alert,
        { attrs: { show: true } },
        [element],
      );
    }

    return h('div', [element]);
  },
};
</script>
