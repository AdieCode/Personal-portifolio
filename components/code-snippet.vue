<template>
    <div>
      <pre>
        <code v-html="highlightedCode"></code>
      </pre>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';  

const highlightedCode = ref('');

function highlightCode(code) {
  // Define your token types and corresponding CSS classes
  const tokenTypes = {
    comment: 'comment',
    // Add more token types as needed
  };

  // Tokenize the code
  let highlighted = code
    .replace(/(\/\/.*$)/gm, `<span class="${tokenTypes.comment}">$1</span>`); // Highlight comments

  return highlighted;
}
const codeExample = `
// This is a JavaScript code snippet
function greet(name) {
  return 'Hello, ' + name + '!';
}

const message = greet('world');
console.log(message);
`;


onMounted(() => {
  highlightedCode.value = highlightCode(codeExample);
});
</script>

<style lang="css" scoped>
.keyword {
  color: blue;
}

.string {
  color: green;
}

.comment {
  color: gray;
  font-style: italic;
}
</style>