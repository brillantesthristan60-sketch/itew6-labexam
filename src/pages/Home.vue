<template>
  <div class="home-page">
    <section class="hero">
      <h2>Welcome to Student Info App</h2>
      <p>This application demonstrates Vue.js components, routing, and API integration.</p>
      <router-link to="/students" class="btn-primary">View Students</router-link>
    </section>

    <section class="features">
      <h3>Features</h3>
      <ul>
        <li>✓ Component-based architecture</li>
        <li>✓ Props and state management</li>
        <li>✓ Client-side routing</li>
        <li>✓ API data fetching with loading states</li>
        <li>✓ Error handling</li>
        <li>✓ Responsive design</li>
      </ul>
    </section>
  </div>
</template>

<script>
export default {
  name: 'HomePage'
}
</script>

<style scoped>
.home-page {
  max-width: 1200px;
  margin: 0 auto;
  padding: 40px 20px;
}

.hero {
  text-align: center;
  padding: 60px 20px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border-radius: 8px;
  margin-bottom: 40px;
}

.hero h2 {
  font-size: 32px;
  margin: 0 0 20px 0;
}

.hero p {
  font-size: 18px;
  margin: 0 0 30px 0;
  opacity: 0.9;
}

.btn-primary {
  display: inline-block;
  background-color: #42b983;
  color: white;
  text-decoration: none;
  padding: 12px 30px;
  border-radius: 4px;
  font-size: 16px;
  transition: background-color 0.3s;
}

.btn-primary:hover {
  background-color: #359970;
}

.features, .info {
  margin-bottom: 40px;
}

.features h3, .info h3 {
  color: #2c3e50;
  font-size: 24px;
  margin-bottom: 20px;
}

.features ul {
  list-style: none;
  padding: 0;
}

.features li {
  padding: 10px 0;
  font-size: 16px;
  color: #555;
  border-bottom: 1px solid #eee;
}

.features li:last-child {
  border-bottom: none;
}

.info-box {
  background-color: #f5f5f5;
  padding: 20px;
  border-radius: 8px;
  border-left: 4px solid #42b983;
}

.info-box p {
  margin: 10px 0;
  color: #333;
}
</style>
