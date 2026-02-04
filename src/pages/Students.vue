<template>
  <div class="students-page">
    <h2>Students List</h2>
    <p class="subtitle">Filipino Students from Cabuyao City, Laguna</p>

    <!-- Loading State -->
    <div v-if="loading" class="loading">
      <p>Loading students...</p>
      <div class="spinner"></div>
    </div>

    <!-- Error State -->
    <div v-else-if="error" class="error-message">
      <p>⚠️ Error: {{ error }}</p>
      <button @click="fetchStudents" class="btn-retry">Retry</button>
    </div>

    <!-- Students List -->
    <div v-else class="students-container">
      <div v-if="students.length === 0" class="no-data">
        <p>No students found.</p>
      </div>
      <student-component
        v-for="student in students"
        :key="student.id"
        :student="student"
      />
    </div>

    <!-- Footer Info -->
    <div class="footer-info">
      <p>Total Students: {{ students.length }}</p>
    </div>
  </div>
</template>

<script>
import StudentComponent from '../components/StudentComponent.vue'

export default {
  name: 'StudentsPage',
  components: {
    StudentComponent
  },
  data() {
    return {
      students: [],
      loading: true,
      error: null
    }
  },
  mounted() {
    this.fetchStudents()
  },
  methods: {
    fetchStudents() {
      this.loading = true
      this.error = null
      
      // Use mock data with Filipino names and Cabuyao City addresses
      const filipinoStudents = [
        {
          id: 1,
          name: 'Maria Santos',
          email: 'maria.santos@email.com',
          phone: '555-0101',
          website: 'example.com',
          username: 'mariasantos',
          company: { name: 'TechCorp Philippines' },
          address: { street: '123 Aguinaldo Street', city: 'Cabuyao City, Laguna' }
        },
        {
          id: 2,
          name: 'Juan Dela Cruz',
          email: 'juan.delacruz@email.com',
          phone: '555-0102',
          website: 'example.com',
          username: 'juandelacruz',
          company: { name: 'Innovation Hub' },
          address: { street: '456 Bonifacio Avenue', city: 'Cabuyao City, Laguna' }
        },
        {
          id: 3,
          name: 'Ana Maria Cruz',
          email: 'ana.cruz@email.com',
          phone: '555-0103',
          website: 'example.com',
          username: 'anacruz',
          company: { name: 'Digital Solutions Inc' },
          address: { street: '789 Rizal Boulevard', city: 'Cabuyao City, Laguna' }
        },
        {
          id: 4,
          name: 'Carlos Villanueva',
          email: 'carlos.villanueva@email.com',
          phone: '555-0104',
          website: 'example.com',
          username: 'carlosv',
          company: { name: 'Software Development Co' },
          address: { street: '321 Quezon Street', city: 'Cabuyao City, Laguna' }
        },
        {
          id: 5,
          name: 'Rosa Reyes',
          email: 'rosa.reyes@email.com',
          phone: '555-0105',
          website: 'example.com',
          username: 'rosareyes',
          company: { name: 'Business Solutions' },
          address: { street: '654 Marcos Highway', city: 'Cabuyao City, Laguna' }
        },
        {
          id: 6,
          name: 'Pedro Santos',
          email: 'pedro.santos@email.com',
          phone: '555-0106',
          website: 'example.com',
          username: 'pedrosantos',
          company: { name: 'Tech Innovations' },
          address: { street: '987 Daang Maharlika', city: 'Cabuyao City, Laguna' }
        },
        {
          id: 7,
          name: 'Sofia Garcia',
          email: 'sofia.garcia@email.com',
          phone: '555-0107',
          website: 'example.com',
          username: 'sofiagarcia',
          company: { name: 'Web Development Studio' },
          address: { street: '147 Salcedo Street', city: 'Cabuyao City, Laguna' }
        },
        {
          id: 8,
          name: 'Miguel Torres',
          email: 'miguel.torres@email.com',
          phone: '555-0108',
          website: 'example.com',
          username: 'migueltorres',
          company: { name: 'IT Consulting Group' },
          address: { street: '258 Osmena Boulevard', city: 'Cabuyao City, Laguna' }
        },
        {
          id: 9,
          name: 'Isabel Mendoza',
          email: 'isabel.mendoza@email.com',
          phone: '555-0109',
          website: 'example.com',
          username: 'isabelmendoza',
          company: { name: 'Digital Marketing Agency' },
          address: { street: '369 Katipunan Avenue', city: 'Cabuyao City, Laguna' }
        },
        {
          id: 10,
          name: 'Antonio Morales',
          email: 'antonio.morales@email.com',
          phone: '555-0110',
          website: 'example.com',
          username: 'antoniom',
          company: { name: 'Cloud Services Ltd' },
          address: { street: '741 Lapu-Lapu Street', city: 'Cabuyao City, Laguna' }
        }
      ]
      
      // Simulate loading delay
      setTimeout(() => {
        try {
          this.students = filipinoStudents
          this.loading = false
        } catch (error) {
          this.error = error.message || 'Failed to load students. Please try again.'
          this.loading = false
          console.error('Error loading students:', error)
        }
      }, 500)
    }
  }
}
</script>

<style scoped>
.students-page {
  max-width: 1200px;
  margin: 0 auto;
  padding: 40px 20px;
}

h2 {
  color: #2c3e50;
  font-size: 28px;
  margin: 0 0 10px 0;
}

.subtitle {
  color: #666;
  margin: 0 0 30px 0;
  font-style: italic;
}

.loading {
  text-align: center;
  padding: 60px 20px;
}

.loading p {
  font-size: 18px;
  color: #666;
  margin-bottom: 20px;
}

.spinner {
  width: 50px;
  height: 50px;
  border: 4px solid #f3f3f3;
  border-top: 4px solid #42b983;
  border-radius: 50%;
  animation: spin 1s linear infinite;
  margin: 0 auto;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

.error-message {
  background-color: #fee;
  border: 1px solid #fcc;
  border-radius: 8px;
  padding: 20px;
  color: #c00;
  text-align: center;
  margin-bottom: 20px;
}

.error-message p {
  margin: 0 0 15px 0;
  font-size: 16px;
}

.btn-retry {
  background-color: #f44336;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 14px;
  transition: background-color 0.3s;
}

.btn-retry:hover {
  background-color: #d32f2f;
}

.students-container {
  display: grid;
  gap: 20px;
}

.no-data {
  text-align: center;
  padding: 40px;
  color: #999;
  font-size: 18px;
}

.footer-info {
  text-align: center;
  margin-top: 30px;
  padding-top: 20px;
  border-top: 1px solid #eee;
  color: #666;
}
</style>
