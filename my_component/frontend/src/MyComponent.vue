<template>
  <v-main class="wrapper">
    <!-- 
      Show a button and some text.
      When the button is clicked, we'll increment our "numClicks" state
      variable, and send its new value back to Streamlit, where it'll
      be available to the Python program.
    -->
    <v-card class="ml-2 mt-1" max-width="344">
      <v-card-title>Hello, {{args.name}}!</v-card-title>
      <v-card-subtitle>This component has a title and a button</v-card-subtitle>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn small primary @click="onClicked()">
          Click Me!
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-main>
</template>

<script>
import { Streamlit } from "streamlit-component-lib";

export default {
  name: "MyComponent",
  props: ["args"], // Arguments that are passed to the plugin in Python are accessible in props `args`. Here, we access the "name" arg.
  data() {
    return {
      numClicks: 0
    };
  },
  methods: {
    /** Click handler for our "Click Me!" button. */
    onClicked: function() {
      // Increment this.numClicks, and pass the new value back to
      // Streamlit via `Streamlit.setComponentValue`.
      this.numClicks++;
      Streamlit.setComponentValue(this.numClicks);
    }
  }
};
</script>
