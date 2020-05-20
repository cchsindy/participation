<template>
  <div id="app">
    <h1>Athletic Participation</h1>
    <h2>Step 1</h2>
    <p>
      Download and print the
      <a
        href="https://ihsaa.org/Portals/0/ihsaa/documents/quick%20resources/2020-21%20Physical%20Form.pdf?ver=2020-01-17-154323-640"
        target="_blank"
      >IHSAA Physical Form</a>,
      complete all 5 pages, and scan or take a picture of each page to upload below.
    </p>
    <p>
      <i>All images must be in JPEG format (.jpg) and less than 4MB each.</i>
    </p>
    <p>
      Upload IHSAA form page 1
      <br />
      <input type="file" />
    </p>
    <p>
      Upload IHSAA form page 2
      <br />
      <input type="file" />
    </p>
    <p>
      Upload IHSAA form page 3
      <br />
      <input type="file" />
    </p>
    <p>
      Upload IHSAA form page 4
      <br />
      <input type="file" />
    </p>
    <p>
      Upload IHSAA form page 5
      <br />
      <input type="file" />
    </p>
    <button>Step 2</button>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {}
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
