<template>
  <div class="student-card">
    <h3>{{ student.name }}</h3>
    <p><strong>ID:</strong> {{ student.id }}</p>
    <p><strong>Email:</strong> {{ student.email }}</p>
    <p><strong>Phone:</strong> {{ student.phone }}</p>
    <p><strong>Website:</strong> {{ student.website }}</p>
    <p><strong>Company:</strong> {{ student.company.name }}</p>
    <button @click="toggleDetails" class="btn">
      {{ showDetails ? 'Hide Details' : 'Show Details' }}
    </button>
    <div v-if="showDetails" class="details">
      <p><strong>Username:</strong> {{ student.username }}</p>
      <p><strong>Address:</strong> {{ student.address.street }}, {{ student.address.city }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'StudentComponent',
  props: {
    student: {
      type: Object,
      required: true,
      default: () => ({
        id: 0,
        name: 'Student Name',
        email: 'email@example.com',
        phone: '000-000-0000',
        website: 'example.com',
        username: 'username',
        company: { name: 'Company' },
        address: { street: 'Street', city: 'City' }
      })
    }
  },
  data() {
    return {
      showDetails: false
    }
  },
  methods: {
    toggleDetails() {
      this.showDetails = !this.showDetails
    }
  }
}
</script>

<style scoped>
.student-card {
  background: white;
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  padding: 20px;
  margin: 15px 0;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s, box-shadow 0.3s;
}

.student-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
}

h3 {
  margin: 0 0 15px 0;
  color: #2c3e50;
  font-size: 20px;
}

p {
  margin: 8px 0;
  color: #333;
  font-size: 14px;
}

.btn {
  background-color: #42b983;
  color: white;
  border: none;
  padding: 10px 15px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 14px;
  margin-top: 10px;
  transition: background-color 0.3s;
}

.btn:hover {
  background-color: #359970;
}

.details {
  background-color: #f5f5f5;
  padding: 12px;
  border-radius: 4px;
  margin-top: 15px;
  border-left: 4px solid #42b983;
}
</style>
