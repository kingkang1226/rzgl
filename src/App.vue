<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app
{
	height: 100%;
	width: 100%;
	position: absolute;

}
body {
	width: 100%;
	height: 100%;
	position: absolute;
	top: 0;
	left: 0;
	margin: 0;
}
</style>
