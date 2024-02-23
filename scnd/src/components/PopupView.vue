<template>
  <div class="overlay" @click="closePopup">
    <div class="popup" @click.stop>
      <h2>Заполните данные</h2>
      <div class="flex-container">
        <div class="column">
          <div v-for="(label, field) in fields[0] " :key="field" class="input-field">
            <label :for="field">{{ label }}:</label>
            <input v-model="formData[field]" :type="field" :id="field">
          </div>
        </div>
        <div class="column">
          <div v-for="(label, field) in fields[1]" :key="field" class="input-field">
            <label :for="field">{{ label }}:</label>
            <input v-model="formData[field ]" :type="field" :id="field">
          </div>
        </div>
      </div>
      <button @click="submitForm">Отправить</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      fields: [
        {
        name: 'Имя',
        email: 'Email',
        },{
        phone: 'Телефон',
        city: 'Город',
        message: 'Сообщение'
        }
    ],
      formData: {
        name: '',
        email: '',
        phone: '',
        city: '',
        message: ''
      }
    };
  },
  methods: {
    closePopup() {
      this.$emit('closePopup');
    },
    submitForm() {
      this.$emit('submitForm', this.formData);
    }
  }
}
</script>

<style scoped>
/* Добавленные стили для колонок и флекс-контейнера */
.input-field{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.flex-container {
  gap:20px;
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}
.column{
  gap:20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-direction: column;
}
@media (max-width: 500px) {
    .flex-container{
        flex-direction: column;
    }
}



.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
}

.popup {
  background-color: #fff;
  padding: 20px;
  max-width: 500px;
  width: 100%;
  text-align: center;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  border-radius: 5px;
  position: relative;
}
</style>
