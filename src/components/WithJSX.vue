<script>
import Alert from 'bootstrap-vue/es/components/alert/alert';
import Badge from 'bootstrap-vue/es/components/badge/badge';
import Link from 'bootstrap-vue/es/components/link/link';

export default {
  name: 'render-function',
  props: ['options'],
  render() {
    const { link, badge, alert } = this.options;

    let element = <span>{this.$slots.default}</span>;

    if (link) {
      element = <Link href={link}>{element}</Link>;
    }

    if (badge) {
      element = (
        <div>
          {element}
          <Badge>{badge}</Badge>
        </div>
      );
    }

    if (alert) {
      element = <Alert show>{element}</Alert>;
    }

    return <div>{element}</div>;
  },
};
</script>
