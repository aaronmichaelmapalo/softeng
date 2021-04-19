<template>
  <breeze-authenticated-layout>
    <template #header>
      <h2 class="font-semibold text-xl text-gray-800 leading-tight">
        Dashboard
      </h2>
    </template>

    <div class="py-2 mt-28  overflow-hidden">
      <div class="mx-auto px-14">
        <div class="bg-white shadow-sm">
          <div class="p-4 bg-white border-b border-gray-200">
            
            <!--TABLE-->
            <a class="text-2xl font-bold p-2 pl-2">Stock Categories</a>
            <inertia-link :href="route('sc.create')">
                    <button class="mx-2 my-2 bg-indigo-700 w-25 transition duration-150 ease-in-out hover:bg-indigo-600 rounded text-white px-5 py-2 text-xs">Create</button>

              </inertia-link>
            <table class="rounded-t m-5 w-5/6 mx-auto bg-gray-200 text-gray-800">
              <tr class="text-left border-b-2 border-gray-300">
                <th class="px-4 py-3">ID</th>
                <th class="px-4 py-3">Description</th>
                <th class="px-4 py-3">Type</th>
                <th class="px-4 py-3">Stock Account</th>
                <th class="px-4 py-3">Date Created</th>
              </tr>
              
              <tr v-for="item in stock_categories" class="hover:bg-white bg-gray-100 border-b border-gray-200">
                <td class="px-4 py-3">{{item.id}}</td>
                <td class="px-4 py-3">{{item.description}}</td>
                <td class="px-4 py-3">{{item.type}}</td>
                <td class="px-4 py-3">{{item.stock_account}}</td>
                <td class="px-4 py-3">{{item.created_at}}</td>
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
    stock_categories: Array,
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
