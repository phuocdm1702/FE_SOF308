<script setup>
import { ref } from 'vue'
import FormComponentSach from '@/component/FormComponentSach.vue';

const listSach = ref(
  [
    {
      "id": "1",
      "ten": "ten 1",
      "loai": "Sách thiếu nhi",
      "tacGia": "tacGia 1",
      "gia": 90
    },
    {
      "id": "2",
      "ten": "ten 2",
      "loai": "Truyện Tranh",
      "tacGia": "tacGia 2",
      "gia": 72
    },
    {
      "id": "3",
      "ten": "ten 3",
      "loai": "Sách Khoa Học",
      "tacGia": "tacGia 3",
      "gia": 71
    },
    {
      "id": "4",
      "ten": "ten 4",
      "loai": "Truyện Tranh",
      "tacGia": "tacGia 4",
      "gia": 71
    },
    {
      "id": "5",
      "ten": "ten 5",
      "loai": "Sách thiếu nhi",
      "tacGia": "tacGia 5",
      "gia": 59
    },
    {
      "id": "6",
      "ten": "ten 6",
      "loai": "Sách Khoa Học",
      "tacGia": "tacGia 6",
      "gia": 67
    },
    {
      "id": "7",
      "ten": "ten 7",
      "loai": "Truyện Tranh",
      "tacGia": "tacGia 7",
      "gia": 90
    },
    {
      "id": "8",
      "ten": "ten 8",
      "loai": "Sách thiếu nhi",
      "tacGia": "tacGia 8",
      "gia": 21
    },
    {
      "id": "9",
      "ten": "ten 9",
      "loai": "Sách Khoa Học",
      "tacGia": "tacGia 9",
      "gia": 80
    },
    {
      "id": "10",
      "ten": "ten 10",
      "loai": "Truyện Tranh",
      "tacGia": "tacGia 10",
      "gia": 29
    },
    {
      "id": "11",
      "ten": "ten 11",
      "loai": "Sách thiếu nhi",
      "tacGia": "tacGia 11",
      "gia": 15
    },
    {
      "id": "12",
      "ten": "ten 12",
      "loai": "Sách Khoa Học",
      "tacGia": "tacGia 12",
      "gia": 74
    },
    {
      "id": "13",
      "ten": "ten 13",
      "loai": "Truyện Tranh",
      "tacGia": "tacGia 13",
      "gia": 94
    },
    {
      "id": "14",
      "ten": "ten 14",
      "loai": "Sách thiếu nhi",
      "tacGia": "tacGia 14",
      "gia": 41
    },
    {
      "id": "15",
      "ten": "ten 15",
      "loai": "Sách Khoa Học",
      "tacGia": "tacGia 15",
      "gia": 31
    },
    {
      "id": "16",
      "ten": "ten 16",
      "loai": "Sách Khoa Học",
      "tacGia": "tacGia 16",
      "gia": 82
    },
    {
      "id": "17",
      "ten": "ten 17",
      "loai": "Truyện Tranh",
      "tacGia": "tacGia 17",
      "gia": 85
    },
    {
      "id": "18",
      "ten": "ten 18",
      "loai": "Sách thiếu nhi",
      "tacGia": "tacGia 18",
      "gia": 7
    },
    {
      "id": "19",
      "ten": "ten 19",
      "loai": "Sách Khoa Học",
      "tacGia": "tacGia 19",
      "gia": 80
    },
    {
      "id": "20",
      "ten": "ten 20",
      "loai": "Truyện Tranh",
      "tacGia": "tacGia 20",
      "gia": 66
    }
  ]
)
const addSachLisst = (newSach) =>{
  listSach.value.push(newSach);
}

const removeSach = (id) =>{
const index = listSach.value.findIndex((sach) => sach.id === id)
listSach.value.splice(index,id)
alert('Xóa thành công.')
}
</script>

<template>
  <FormComponentSach :listLoai="listSach" @addBook="addSachLisst" />
  <div class="container mt-5">
    <table class="table table-striped table-hover">
      <thead class="table-dark">
        <tr>
          <th>ID</th>
          <th>Tên</th>
          <th>Loại</th>
          <th>Tác giả</th>
          <th>Giá</th>
          <th>Chức năng</th>
        </tr>
      </thead>
      <tbody>
        <template v-for="sach in listSach" :key="sach.id">
          <tr>
            <td>{{ sach.id }}</td>
            <td>{{ sach.ten }}</td>
            <td>{{ sach.loai }}</td>
            <td>{{ sach.tacGia }}</td>
            <td>{{ sach.gia }}</td>
            <td>
              <button class="btn btn-danger btn-sm" @click="removeSach(sach.id)">Remove</button>
            </td>
          </tr>
        </template>
      </tbody>
    </table>
  </div>

</template>
