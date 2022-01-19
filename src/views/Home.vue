<template>
  <div class="home">
    <!-- Creating organisation step 1 : create company -->

    <div
      class="createCompanyForm wh-form"
      v-if="formSection == 'createCompany'"
    >
      <div class="formHeader">
        <h2>Create company/organisation.</h2>
        <p>Enter all the details to create organisation.</p>
      </div>

      <label for="organisationName">Name: </label><br />
      <input
        type="text"
        id="orgName"
        v-model="orgName"
        name="organisationName"
        placeholder="Enter name of organisation."
        autocomplete="off"
      /><br /><br />

      <label for="organisationDomain">Domain: </label><br />
      <input
        type="text"
        id="orgDomain"
        v-model="orgDomain"
        name="organisationDomain"
        placeholder="Enter domain for organisation."
        autocomplete="off"
      /><br /><br />
      <button class="submitBtn" v-on:click="createOrganisation()">
        SUBMIT
      </button>
    </div>

    <!-- Creating organisation step 2 : create warehouse -->

    <div
      class="createWarehouseForm wh-form"
      v-if="formSection == 'createWarehouse'"
    >
      <div class="formHeader">
        <h2>Create warehouse.</h2>
        <p>Enter all the details to create warehouse for the organisation.</p>
      </div>

      <label for="warehouseName">Warehouse name: </label><br />
      <input
        type="text"
        id="wh-Name"
        v-model="whName"
        name="warehouseName"
        placeholder="Enter an alias for warehouse."
        autocomplete="off"
      /><br /><br />

      <label for="addAisle">Add aisle: {{ aisleCount }} </label><br />
      <input
        type="number"
        v-for="el in aisleCount"
        class="aisleNumber"
        :key="el"
        placeholder="Enter location quantity"
      />
      <button class="addAisleBtn" v-on:click="aisleCount++">+</button>

      <br /><br />

      <button class="submitBtn" @click="createWarehouse()">SUBMIT</button>
    </div>
  </div>
</template>


<script>
export default {
  name: "Home",
  components: {},
  data() {
    return {
      formSection: "createCompany",

      orgName: "",
      orgDomain: "",

      whName: "",
      aisleCount: 1,
      aisles: {},
    };
  },
  methods: {
    createOrganisation: function () {
      this.formSection = "createWarehouse";
    },

    createWarehouse: function () {
      var data = {
        name: this.whName,
        aisle: [],
      };
      var totalAisle = document.getElementsByClassName("aisleNumber");
      var tempArray = [...totalAisle];
      tempArray.map((el) => {
        if (el.value != "") data.aisle.push({ location_qty: el.value });
      });
      console.log(data);
    },
  },
};
</script>


<style scoped>
.addAisleBtn {
  padding: 15px;
  background-color: rgb(106, 13, 255);
  color: white;
  border: none;
  border-radius: 4px;
  outline: none;
}
.aisleNumber {
  margin-right: 10px;
}
.wh-form {
  width: 60vw;
  margin: 50px 100px;
}
.formHeader {
  margin-bottom: 40px;
}
.formHeader::after {
  content: "";
  position: absolute;
  height: 3px;
  width: 80px;
  background-color: rgb(98, 0, 255);
}
.formHeader > h2 {
  padding-bottom: 0;
  margin-bottom: 0;
}
.formHeader > p {
  margin-top: 5px;
  padding-top: 0;
}
input {
  margin-top: 10px;
  padding: 15px 15px;
  border: 1px solid rgb(106, 13, 255);
  border-radius: 4px;
  width: 250px;
  color: rgb(78, 78, 78);
  letter-spacing: 1px;
  outline: none;
}
.submitBtn {
  padding: 12px 28px;
  background-color: rgb(106, 13, 255);
  letter-spacing: 1.2px;
  font-size: 12px;
  color: white;
  border: none;
  border-radius: 2px;
}
</style>


