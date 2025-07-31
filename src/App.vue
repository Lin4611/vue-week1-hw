<script setup>
import { ref, toValue } from 'vue';
const menus = ref([
  { id: 1 ,name:"珍珠奶茶",detail:"香濃奶茶搭配QQ珍珠",price: 50,stock:20,isEditing: false },
  { id: 2,name:"冬瓜檸檬",detail:"清新冬瓜配上新鮮檸檬",price: 45,stock:18,isEditing: false },
  { id: 3,name:"翡翠檸檬",detail:"綠茶與檸檬的完美結合",price: 55,stock:34, isEditing: false },
  { id: 4,name:"四季春茶",detail:"香醇四季春茶，回甘無比",price: 45,stock:10, isEditing: false },
  { id: 5,name:"阿薩姆奶茶",detail:"阿薩姆紅茶搭配香醇鮮奶",price: 50,stock:25, isEditing: false },
  { id: 6,name:"檸檬冰茶",detail:"檸檬與冰茶的清新組合",price: 45,stock:25,isEditing: false },
  { id: 7,name:"芒果綠茶",detail:"芒果與綠茶的獨特風味",price: 55,stock:18, isEditing: false },
  { id: 8,name:"抹茶拿鐵",detail:"抹茶與鮮奶的絕配",price: 60,stock:20,isEditing: false }
]);
const add = (menu) => {
    menu.stock++;
};
const minus = (menu) => {
    if (menu.stock > 0) {
        menu.stock--;
    }else {
        alert("庫存不足");
    }
};

const edit = (item) => {
    item.isEditing = !item.isEditing;
};


</script>

<template>
  <table>
  <thead>
    <tr>
      <th scope="col">品項</th>
      <th scope="col">描述</th>
      <th scope="col">價格</th>
      <th scope="col">庫存</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for ="menu in menus" :key="menu.id">
      <td v-if="menu.isEditing">
        <input type="text" v-model="menu.name"/>
      </td>
      <td v-else>{{ menu.name }}</td>
      <td>{{ menu.detail }}</td>
      <td>{{ menu.price }} 元</td>
      <td>
        <button type="button" @click="minus(menu)">-</button>
        {{ menu.stock }}
        <button type="button" @click="add(menu)">+</button>
      </td>
      <td>
        <button class="edit-btn" type="button" title="修改" @click="edit(menu)" >
          {{ menu.isEditing ? '✅':'✏️' }}
        </button>
      </td>
    </tr>
  </tbody>
</table>
</template>

<style scoped>

table {
  font-family: 'Copperplate', sans-serif;
  background-color: #f9f9f9;
  color: #333;
  font-size: 16px;
  padding: 20px;  
  border-spacing: 12px 12px;
}
button {
  padding: 12px 12px;
  background-color: #00cec9;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
}

button:hover {
  background-color: #0984e3;
  transform: scale(1.05);
}

button:active {
  transform: scale(0.97);
}

button:disabled {
  background-color: #b2bec3;
  cursor: not-allowed;
}

.edit-btn {
  background-color: #3498db;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 6px;
  font-size: 14px;
  cursor: pointer;
  transition: background-color 0.2s ease;
}
.edit-btn:hover {
  background-color: #2980b9;
}


header {
  line-height: 1.5;
}

tr {
  background-color: white;
}

td {
  border-radius: 6px;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
  padding: 12px;
}


.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
