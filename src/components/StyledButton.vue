<script>
export default {
  name: "StyledButton",
};
</script>

<template>
  <a>
    <span></span>
    <span></span>
    <span></span>
    <span></span>
    <slot></slot>
  </a>
</template>

<style>
a {
  font-family: "Unbounded", cursive;
  position: relative;
  display: inline-block;
  padding: 12px 16px;
  color: #eebbb7;
  cursor: pointer;
  text-transform: uppercase;
  text-decoration: none;
  font-size: 0.8em;
  font-weight: 400;
  overflow: hidden;
  transition: 0.2s;
  width: fit-content;
}

a:hover {
  color: #601733;
  background: #eebbb7;
  box-shadow: 0 0 5px #eebbb7, 0 0 10px #eebbb7, 0 0 20px #eebbb7;
  transition-delay: 1s;
}

a span {
  position: absolute;
  display: block;
}

a span:nth-child(1) {
  top: 0;
  left: -100%;
  width: 100%;
  height: 3px;
  background: linear-gradient(90deg, transparent, #eebbb7);
}

a:hover span:nth-child(1) {
  left: 100%;
  transition: 1s;
}

a span:nth-child(3) {
  bottom: 0;
  right: -100%;
  width: 100%;
  height: 3px;
  background: linear-gradient(270deg, transparent, #eebbb7);
}

a:hover span:nth-child(3) {
  right: 100%;
  transition: 1s;
  transition-delay: 0.5s;
}

a span:nth-child(2) {
  top: -100%;
  right: 0;
  width: 3px;
  height: 100%;
  background: linear-gradient(180deg, transparent, #eebbb7);
}

a:hover span:nth-child(2) {
  top: 100%;
  transition: 1s;
  transition-delay: 0.25s;
}

a span:nth-child(4) {
  bottom: -100%;
  left: 0;
  width: 3px;
  height: 100%;
  background: linear-gradient(360deg, transparent, #eebbb7);
}

a:hover span:nth-child(4) {
  bottom: 100%;
  transition: 1s;
  transition-delay: 0.75s;
}
</style>
