<template>
<div>
<Layout>
    <div class="flex justify-center w-full">
        <div class="bg-white flex flex-col w-1/3 mt-20 p-6">
            <h2 class="text-lg">Stock Form</h2>
            <form id="stock-form" name="stock-form" v-on:submit.prevent="submit">
                <div class="flex flex-col pt-6">
                    <label for="id">ID</label>
                    <input type="text" name="id" id="id" v-model="form.id" autocomplete="off"/>
                    <div class="text-red-700 text-sm" >
                        {{errors.id}}
                    </div>
                </div>

                <div class="flex flex-col pt-6">
                    <label for="stock_category_id">Stock Category ID</label>
                    <select name="stock_category_id" id="stock_category_id" v-model="form.stock_category_id">
                        <option v-for="item in stock_categories" v-bind:value="item.id">
                            {{ item.id }}, {{ item.description }}
                        </option>
                    </select>
                    <div class="text-red-700 text-sm" >
                        {{errors.category_id}}
                    </div>
                </div>
                
                <div class="flex flex-col pt-6">
                    <label for="description">Description</label>
                    <input type="text" name="description" id="description" v-model="form.description" autocomplete="off"/>
                    <div class="text-red-700 text-sm">
                        {{errors.description}}
                    </div>
                </div>

                <div class="flex flex-col pt-6">
                    <label for="uom">Unit of Measurement</label>
                    <input type="text" name="uom" id="uom" v-model="form.uom" autocomplete="off"/>
                    <div class="text-red-700 text-sm">
                        {{errors.uom}}
                    </div>
                </div>

                <div class="flex flex-col pt-6">
                    <label for="barcode">Barcode</label>
                    <input type="text" name="barcode" id="barcode" v-model="form.barcode" autocomplete="off"/>
                    <div class="text-red-700 text-sm">
                        {{errors.barcode}}
                    </div>
                </div>

                <div class="flex items-center pt-6">
                    <input type="checkbox" id="discontinued" name="discontinued" value="Y" v-model="form.discontinued" >
                    <label for="discontinued">&nbsp;Discontinued?</label>
                    <div class="text-red-700 text-sm">
                        {{errors.discontinued}}
                    </div>
                </div>

                <div class="flex flex-col pt-6">
                    <label for="photo_path">Photo</label>
                    <input type="text" name="photo_path" id="photo_path" v-model="form.photo_url" autocomplete="off"/>
                    <div class="text-red-700 text-sm">
                        {{errors.photo_url}}
                    </div>
                </div>

                <div class="flex flex-col pt-6">
                    <button type="submit" class="bg-indigo-800 text-white p-2">Save</button>
                </div>


            </form>
        </div>
    </div>
    
</Layout>
</div>
</template>

<script>
    import { ref, reactive } from 'vue';
    import Layout from "@/Layouts/Layout.vue";
    import { Inertia } from "@inertiajs/inertia";

    export default {

        components:{
            Layout, 
        },

        props:{
            stock_categories: Array,
            errors:Object,
        },

        setup(props, context){

            const form = reactive({
                id:null,
                stock_category_id:null,
                description:null,
                uom:null,
                barcode:null,
                discontinued:"N",
                photo_path:null,
            });

            const submit = () => {
                  Inertia.post(route("stock.store"), form);
            };

            return{
                form,
                submit,

            }

        },

    }
</script>

<style>

</style>