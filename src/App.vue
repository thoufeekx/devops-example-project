<template>
  <div class="app">
    <header>
      <h1>DevOps Example Project</h1>
      <p class="subtitle">A Test Project for CI/CD Implementation</p>
    </header>
    
    <main>
      <div class="card">
        <h2>🎯 Project Features</h2>
        <div class="features-grid">
          <div class="feature-item">
            <h3>Automated Testing</h3>
            <p>Continuous testing ensures code quality and reliability</p>
          </div>
          <div class="feature-item">
            <h3>Build Process</h3>
            <p>Streamlined build process for consistent deployments</p>
          </div>
          <div class="feature-item">
            <h3>Deployment</h3>
            <p>Automated deployment pipeline for quick releases</p>
          </div>
        </div>
      </div>

      <div class="card">
        <h2>📝 Latest Updates</h2>
        <div class="updates-list">
          <div class="update-item">
            <span class="date">29 Jan 2025</span>
            <p>Initial project setup with Vue.js frontend</p>
          </div>
          <div class="update-item">
            <span class="date">29 Jan 2025</span>
            <p>Added CI/CD configuration files</p>
          </div>
          <div class="update-item">
            <span class="date">29 Jan 2025</span>
            <p>Implemented automated build process</p>
          </div>
        </div>
      </div>

      <div class="card">
        <h2>ℹ️ About This Project</h2>
        <p>This example project demonstrates modern DevOps practices including:</p>
        <ul>
          <li>Updated: Continuous Integration practices</li>
          <li>Updated: Automated Testing procedures</li>
          <li>Updated: Deployment automation</li>
          <li>Updated:Modern frontend development with Vue.js</li>
        </ul>
      </div>
    </main>

    <footer>
      <p>Updated Project Example Project - Created for DevOps Testing</p>
    </footer>
  </div>
</template>

<style scoped>
.app {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
  font-family: Arial, sans-serif;
  color: #2c3e50;
}

header {
  text-align: center;
  margin-bottom: 3rem;
  padding: 2rem 0;
  background: linear-gradient(to right, #3498db, #2ecc71);
  color: white;
  border-radius: 8px;
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 0.5rem;
}

.subtitle {
  font-size: 1.2rem;
  opacity: 0.9;
}

.card {
  background: white;
  border-radius: 8px;
  padding: 2rem;
  margin-bottom: 2rem;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.1);
}

h2 {
  margin-bottom: 1.5rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.feature-item {
  padding: 1.5rem;
  background: #f8f9fa;
  border-radius: 8px;
  transition: transform 0.2s;
}

.feature-item:hover {
  transform: translateY(-5px);
}

.feature-item h3 {
  color: #3498db;
  margin-bottom: 1rem;
}

.updates-list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.update-item {
  display: flex;
  gap: 1rem;
  padding: 1rem;
  background: #f8f9fa;
  border-radius: 6px;
}

.date {
  color: #666;
  font-size: 0.9rem;
  min-width: 100px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin-bottom: 0.8rem;
  padding-left: 1.5rem;
  position: relative;
}

li::before {
  content: "→";
  position: absolute;
  left: 0;
  color: #3498db;
}

footer {
  text-align: center;
  margin-top: 3rem;
  padding-top: 2rem;
  border-top: 1px solid #eee;
  color: #666;
}
</style>

<script setup>
</script>
