<script>
import map from 'lodash/map';
import Inputs from './components/Inputs';
import FullTemplate from './components/FullTemplate';
import RenderFunction from './components/RenderFunction';
import WithJSX from './components/WithJSX';
import Functional from './components/Functional';

export default {
  name: 'app',
  data() {
    return {
      inputs: {},
      tabs: {
        'Full Template': FullTemplate,
        'Render Function': RenderFunction,
        'With JSX': WithJSX,
        'Functional Component': Functional,
      },
    };
  },
  computed: {
    stringInputs() {
      return JSON.stringify(this.inputs);
    },
    text() {
      return this.inputs.text || '<<No Text>>';
    },
  },
  render() {
    return (
      <b-container fluid>
        <div>{this.stringInputs}</div>
        <Inputs
          // Replicates the behavior of v-model
          value={this.inputs}
          onInput={(inputs) => { this.inputs = inputs; }}
        ></Inputs>
        <b-tabs>
          {map(this.tabs, (Ctor, label) => (
            <b-tab title={label}>
              <Ctor options={this.inputs}>{this.text}</Ctor>
            </b-tab>
          ))}
        </b-tabs>
      </b-container>
    );
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
</style>
