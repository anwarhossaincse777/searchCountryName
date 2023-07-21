<script setup>


import CountryApi from "../CountryApi.js";


const apiResponse = CountryApi;

const countryNameStartWithB = () => apiResponse.filter((item) => item.country.toLowerCase().startsWith('b'));

let total = `There are total number of country: ${apiResponse.length}.  Let's find how much starts with "B"`;
let weFind=`We have found the country starts with "B" are : ${countryNameStartWithB().length}`
</script>


<template>

  <div class="container">
    <h2 class="text-center bg-primary p-4 text-white mt-2">Welcome to Country Api</h2>
    <div class="row mt-5">

      <div class="col-md-6">
        <h2 class="bg-success p-2 text-white mt-lg-1 text-center">List Of Name fo all Country</h2>

        <h6>   {{total}}</h6>

        <table class="table table-dark table-striped">
           <thead>
          <tr>
            <th scope="col">Serial No</th>
            <th scope="col">Country</th>
            <th scope="col">City</th>
          </tr>
          </thead>
          <tbody>
          <tr v-for="(list,index) in apiResponse" :key="index">
            <th scope="row">{{ index + 1 }}</th>
            <td>{{ list.country }}</td>
            <td>{{ list.city }}</td>
          </tr>
          </tbody>
        </table>
      </div>

      <div class="col-md-6">

        <h2 class="bg-danger p-2 text-white mt-lg-1 text-center">Country Name starts with B</h2>
        <h4>{{weFind}}</h4>
        <table class="table table-striped">
          <thead>
          <tr>
            <th scope="col">Serial No</th>
            <th scope="col">Country</th>
            <th scope="col">City</th>
          </tr>
          </thead>
          <tbody>
          <tr v-for="(item,index) in countryNameStartWithB()" :key="index">
            <th scope="row">{{index+1}}</th>
            <td>{{item.country}}</td>
            <td>{{item.city}}</td>
          </tr>

          </tbody>
        </table>
      </div>

    </div>
  </div>


</template>


<style scoped>

</style>