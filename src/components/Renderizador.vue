<script setup lang="ts">
// defineProps<{ msg: string }>()
import cytoscape from 'cytoscape';
import { onMounted } from 'vue';

import Hidrometro from '../assets/Hidrometro.png'


onMounted(() => {
  cytoscape({

    container: document.getElementById('cy'), // container to render in

    elements: [ // list of graph elements to start with
      { // node a
        data: { id: 'ligada' }
      },
      { // node b
        data: { id: 'b' }
      },
      { // edge ab
        data: { id: 'ab', source: 'ligada', target: 'b' }
      }
    ],

    style: [ // the stylesheet for the graph
      {
        selector: 'node',
        style: {
          'label': 'data(id)',
          "background-image": Hidrometro,
          'width': 50,
          'height': 50,
        }
      },

      {
        selector: 'edge',
        style: {
          'width': 2,
          'line-color': '#083A5C',
          'target-arrow-shape': 'none',
          'curve-style': 'taxi',
        }
      }
    ],
  });
})

</script>

<template>
  <div class="container">
    <div id="cy"></div>
  </div>
</template>

<style scoped>
.container {
  width: 100%;
  display: flex;
  justify-content: center;
}

#cy {
  margin-top: 50px;
  width: 500px;
  height: 500px;
  border: rgba(0, 0, 0, 0.164) solid 1px;
  border-radius: 10px;
}
</style>
