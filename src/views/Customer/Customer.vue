<template>
  <div class="containPage" v-if="isLogin">
    <h2>Danh sách người dùng</h2>
    <div class="contentPage" :style="`${isLogin ? '' : 'display: none'}`">
      <a-tabs v-model:activeKey="activeKey">
        <a-tab-pane key="1" tab="Độc giả">
          <h4>Danh sách độc giả</h4>
          <a-table :dataSource="data" :columns="columns" rowKey="_id">
             <!-- Slot cho cột cuối cùng -->
          <template  #action="{ record }" >
              <span class="action_group">
                <a class="text-danger" @click="handleDelete(record)">Xóa</a>
              </span>
          </template>
          </a-table>
        </a-tab-pane>
        <a-tab-pane key="2" tab="Nhân viên" force-render>
          <h4>Danh sách nhân viên</h4>
          <a-table :dataSource="dataStaff" :columns="columnsStaff" rowKey="_id">
         
          </a-table>
        </a-tab-pane>
      </a-tabs>
    </div>
  </div>
  <div v-else class="denied">
    <h3 class="text-center mt-5">Vui lòng đăng nhập để xử dụng dịch vụ</h3>
  </div>


    <!-- Modal Delete NXB -->
    <a-modal
        style="top: 40px"
        v-model:open="isModalDelete"
        title="Xóa sách"
        @ok="handleOkDelete"
        @cancel="handleCancelDelete"
        :ok-button-props="okButtonProps"
        okText="Xác nhận"
        okType= 'danger',
        cancelText="Đóng"
      >
        <p>Bạn có chắc muốn xóa NXB này ?</p>
      </a-modal>

</template>

<script setup>
import { ref } from "vue";
import axios from "axios";
import { toast } from "vue3-toastify";

const activeKey = ref("1");
const data = ref([]);
const dataStaff = ref([]);
const isModalDelete = ref(false);
const idDelete = ref("");
const showModalDelete = () => {
    isModalDelete.value = true;
  };
const handleCancelDelete = () => {
    isModalDelete.value = false;
  };
const isLogin = localStorage.getItem("isLogin");

const columns = [
  {
    title: "Id đọc giả",
    dataIndex: "_id",
    key: "_id",
  },
  {
    title: "Tên",
    dataIndex: "Ten",
    key: "Ten",
  },
  {
    title: "Ngày sinh",
    dataIndex: "NgaySinh",
    key: "NgaySinh",
  },
  {
    title: "Giới tính",
    dataIndex: "Phai",
    key: "Phai",
  },
  {
    title: "Số điện thoại",
    dataIndex: "DienThoai",
    key: "DienThoai",
  },
  {
    title: "Địa chỉ",
    dataIndex: "DiaChi",
    key: "DiaChi",
  },
  {
    title: 'Action',
    key: 'action',
    slots: {
      customRender: 'action',
    },
  },
];

const columnsStaff = [
  {
    title: "Id user",
    dataIndex: "_id",
    key: "_id",
  },
  {
    title: "Họ tên",
    dataIndex: "HoTenNv",
    key: "HoTenNv",
  },
  {
    title: "Chức vụ",
    dataIndex: "ChucVu",
    key: "ChucVu",
  },
  {
    title: "Số điện thoại",
    dataIndex: "SoDienThoai",
    key: "SoDienThoai",
  },
  {
    title: "Địa chỉ",
    dataIndex: "DiaChi",
    key: "DiaChi",
  },

];

const fetchData = () => {
  axios
    .get("http://localhost:3000/reader")
    .then((res) => {
      data.value = res.data;
    })
    .catch((err) => console.log(err));
};

const fetchDataStaff = () => {
  axios
    .get("http://localhost:3000/reader/admin")
    .then((res) => {
      dataStaff.value = res.data;
    })
    .catch((err) => console.log(err));
};

fetchData();
fetchDataStaff();
const handleDelete = (record) => {
  idDelete.value = record._id
  console.log(idDelete.value);
  showModalDelete();
};

const handleOkDelete = () => {
  const id = idDelete.value;
  axios
    .delete("http://localhost:3000/authentication/delete/" + id)
    .then((res) => {
        if (res.data.error) {
          toast.error(res.data.error);
        } else if (res.data.message) {
          toast.success(res.data.message);
          fetchData();

        }
      })
      .catch((err) => console.log(err));
}
</script>

<style lang="scss" scoped>
@import "./Customer.scss";
</style>