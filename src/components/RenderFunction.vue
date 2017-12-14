<script>
import Alert from 'bootstrap-vue/es/components/alert/alert';
import Badge from 'bootstrap-vue/es/components/badge/badge';
import Link from 'bootstrap-vue/es/components/link/link';

export default {
  name: 'render-function',
  props: ['options'],
  render(createElement) {
    const { link, badge, alert } = this.options;

    let element = createElement('span', this.$slots.default);

    if (link) {
      element = createElement(Link, { props: { href: link } }, [element]);
    }

    if (badge) {
      element = createElement('div', [
        element,
        createElement(Badge, badge),
      ]);
    }

    if (alert) {
      element = createElement(
        Alert,
        { attrs: { show: true } },
        [element],
      );
    }

    return createElement('div', [element]);
  },
};
</script>
