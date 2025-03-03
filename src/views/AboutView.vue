<template>
  <div class="about">
    <div class="card">
      <h2>About This Site</h2>
      <div class="content">
        <h3>What It Is</h3>
        <p>An exercise in public API consumption, frontend JavaScript, AWS static site hosting, and
          CI/CD.</p>
        <br>
        <h3>What It Isn't</h3>
        <p>A production-grade tool for collecting accurate information.</p>
        <p>An exercise in web design or accessibility.</p>
        <br>
        <h3>Tech Used</h3>
        <p><strong>API: </strong><a href="https://documents.worldbank.org/en/publication/documents-reports/api">World
        Bank Documents and Report API</a></p>
        <p><strong>Frontend: </strong>Vue 3 and Vite</p>
        <p><strong>Hosting: </strong>AWS S3 and CloudFront</p>
        <p><strong>DNS: </strong>Cloudflare</p>
        <p><strong>CI/CD: </strong>AWS CodeBuild</p>
        <p><strong>Version Control: </strong>GitHub</p>
        <br>
        <h3>Some Notes</h3>
        <p>Some countries seem to have broken since I first set up the map.</p>
        <p>Since this isn't meant to be used as an actual tool, I don't intend to maintain its
          function very diligently.</p>
        <p>I might fix this at some point, but it isn't a priority.</p>
      </div>
    </div>
  </div>
</template>

<style>
.content {
  margin: auto;
  max-width: 640px;
}
.content p, h3 {
  text-align: center;
}
</style>
