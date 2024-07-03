<!-- src/components/ExcelReader.vue 
Vue component that will allow users to upload an Excel file and read its content -->
<template>
    <div>
      <input type="file" @change="handleFileUpload" />
      <table v-if="data.length" class="table table-bordered mt-3">
        <thead>
          <tr>
            <th v-for="(value, key) in data[0]" :key="key">{{ key }}</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(row, index) in data" :key="index">
            <td v-for="(value, key) in row" :key="key">{{ value }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  import { readExcelFile } from '../utils/excel';
  
  export default {
    name: 'ExcelReader',
    setup() {
      const data = ref([]);
  
      const handleFileUpload = async (event) => {
        const file = event.target.files[0];
        if (file) {
          data.value = await readExcelFile(file);
        }
      };
  
      return {
        data,
        handleFileUpload
      };
    }
  };
  </script>
  
  <style scoped>
  .table {
    width: 100%;
    margin-top: 20px;
  }
  </style>