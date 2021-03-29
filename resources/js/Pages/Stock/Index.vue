<template>
  <breeze-authenticated-layout>
    <template #header>
      <h2 class="font-semibold text-xl text-gray-800 leading-tight">
        Dashboard
      </h2>
    </template>

    <div class="py-2 mt-28  overflow-hidden">
      <div class="mx-auto px-8">
        <div class="bg-white shadow-sm">
          <div class="p-8 bg-white border-b border-gray-200">
            
            <!--TABLE-->
            <a class="text-2xl font-bold">Stocks</a>
            <table class="w-full table-auto rounded-t m-5 w-5/6 mx-auto bg-gray-200 text-gray-800">
              <tr class="text-left border-b-2 border-gray-300">
                <th class="px-4 py-3">ID</th>
                <th class="px-4 py-3">Category ID</th>
                <th class="px-4 py-3">Description</th>
                <th class="px-4 py-3">UOM</th>
                <th class="px-4 py-3">Barcode</th>
                <th class="px-4 py-3">Discontinued</th>
                <th class="px-4 py-3">Created at</th>
                <th class="px-4 py-3">Updated at</th>
              </tr>
              
              <tr v-for="item in stock" class="hover:bg-white bg-gray-100 border-b border-gray-200">
                <td class="px-4 py-3">{{item.id}}</td>
                <td class="px-4 py-3">{{item.stock_category_id}}</td>
                <td class="px-4 py-3">{{item.description}}</td>
                <td class="px-4 py-3">{{item.uom}}</td>
                <td class="px-4 py-3">{{item.barcode}}</td>
                <td class="px-4 py-3">{{item.discontinued}}</td>
                <td class="px-4 py-3">{{item.created_at}}</td>
                <td class="px-4 py-3">{{item.updated_at}}</td>
              </tr> 

            </table>
          </div>
        </div>
      </div>
    </div>

  </breeze-authenticated-layout>
</template>

<script>
import Layout from "@/Layouts/Layout.vue";

export default {

  props:{
    stock: Array,
  },
  layout:Layout,
};
</script>

<style scoped>
td:hover{
  cursor: default;
}
th:hover{
  cursor: default;
}
</style>
