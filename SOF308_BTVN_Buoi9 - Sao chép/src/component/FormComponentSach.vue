<script setup>
import { ref, defineProps, defineEmits } from 'vue';

const listLoaiSach = defineProps({
  listLoai: Array
});

const eventAddSach = defineEmits(['addBook']);

const tenSach = ref('');
const loaiSach = ref('');
const tacGiaSach = ref('');
const giaSach = ref('');

const addSachNew = () => {

  if (!tenSach.value.trim()) {
    alert('Vui lòng nhập tên sách');
    return;
  }
  if (!loaiSach.value.trim()) {
    alert('Vui lòng chọn loại sách');
    return;
  }
  if (!tacGiaSach.value.trim()) {
    alert('Vui lòng nhập tên tác giả');
    return;
  }
  if (!giaSach.value || isNaN(giaSach.value) || giaSach.value <= 0) {
    alert('Vui lòng nhập giá sách hợp lệ');
    return;
  }
  const newSach = {
    id: listLoaiSach.listLoai.length + 1,
    ten: tenSach.value,
    loai: loaiSach.value,
    tacGia: tacGiaSach.value,
    gia: Number(giaSach.value)
  };


  eventAddSach('addBook', newSach);
  alert(`Thêm sách "${newSach.ten}" thành công!`);

  tenSach.value = '';
  loaiSach.value = '';
  tacGiaSach.value = '';
  giaSach.value = '';

};


</script>

<template>
  <div class="container mt-5">
    <h1 class="mb-4">Quản lý Sách</h1>
    <form @submit.prevent="addSachNew" class="mb-4">
      <div class="mb-3">
        <label class="form-label">Tên:</label>
        <input v-model="tenSach" type="text" class="form-control" placeholder="Nhập tên sách" />
      </div>

      <div class="mb-3">
        <label class="form-label">Loại:</label>
        <select v-model="loaiSach" class="form-select">
          <option value="" disabled>Chọn loại sách</option>
          <option value="Sách thiếu nhi">Sách thiếu nhi</option>
          <option value="Truyện Tranh">Truyện Tranh</option>
          <option value="Sách Khoa Học">Sách Khoa Học</option>

        </select>
      </div>

      <div class="mb-3">
        <label class="form-label">Tác giả:</label>
        <input v-model="tacGiaSach" type="text" class="form-control" placeholder="Nhập tên tác giả" />
      </div>

      <div class="mb-3">
        <label class="form-label">Giá:</label>
        <input v-model="giaSach" type="number" class="form-control" placeholder="Nhập giá sách" />
      </div>

      <button type="submit" class="btn btn-primary">Thêm Sách</button>
    </form>
  </div>
</template>
