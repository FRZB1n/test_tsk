<template>
  <div>
      <button class="start-btn" @click="openPopup">Начать</button>

      <popup v-if="isPopupVisible" @closePopup="closePopup" @submitForm="submitForm" />
      <output-data v-if="isDataVisible" :data="formData" />
    </div>
  
</template>

<script>
import Popup from '../components/PopupView.vue';
import OutputData from '../components/OutputData.vue';

export default {
  components: {
    Popup,
    OutputData
  },
  data() {
    return {
      isPopupVisible: false,
      isDataVisible: false,
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
    openPopup() {
      this.isPopupVisible = true;
    },
    closePopup() {
      this.isPopupVisible = false;
    },
    submitForm(data) {
      this.formData = data;
      this.isPopupVisible = false;
      this.isDataVisible = true;
    }
  }
}
</script>
<style scoped>

.start-btn {
  margin-top: 200px;
  padding: 10px 20px;
  font-size: 16px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 5px;
  outline: none;
}
</style>