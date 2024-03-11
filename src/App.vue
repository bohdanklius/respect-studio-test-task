<template>
  <div id="app">
    <LoadingProgress />
    <Header />
    <ConsitentLeads />
  </div>
</template>

<script>
import LoadingProgress from "./components/LoadingProgress.vue";
import Header from "./components/Header.vue";
import ConsitentLeads from "./components/ConsitentLeads.vue";

export default {
  name: "App",
  components: {
    LoadingProgress,
    Header,
    ConsitentLeads,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

html,
body,
div,
span,
button,
object,
iframe,
figure,
h1,
h2,
h3,
h4,
h5,
h6,
p,
blockquote,
pre,
a,
code,
em,
img,
small,
strike,
strong,
sub,
sup,
tt,
b,
u,
i,
ol,
ul,
li,
fieldset,
form,
label,
table,
caption,
tbody,
tfoot,
thead,
tr,
th,
td,
main,
canvas,
embed,
footer,
header,
nav,
section,
video,
input {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font-family: inherit;
  vertical-align: baseline;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  text-size-adjust: none;
}

body {
  overflow: auto;
  font-family: "SuisseIntl-Regular", sans-serif;
}

body.lock {
  overflow: hidden;
}

@font-face {
  font-family: "SuisseIntl-Regular";
  src: url("./assets/fonts/SuisseIntl-Regular.woff") format("woff");
  font-weight: normal;
  font-style: normal;
}

.section {
  min-width: 1366px;
  max-width: 1920px;
  margin: 0 auto;
}
</style>
