<template>
  <main>
    <h1>So-and-so's Party!</h1>

    <table>
      <thead>
        <tr>
          <th>Name</th>
          <th>Last name</th>
          <th>Dish</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="guest in guests" :key="guest.id">
          <td>{{ guest.firstname }}</td>
          <td>{{ guest.lastname }}</td>
          <td>{{ guest.dish }}</td>
        </tr>
      </tbody>
    </table>

    <section class="add-more">
      <p>Add guests</p>
      <form>
        <label for="fistname">Name:</label><br />
        <input
          type="text"
          id="fistname"
          name="fistname"
          v-model="newGuests.firstname"
        required/><br />

        <label for="lastname">Last name:</label><br />
        <input
          type="text"
          id="lastname"
          name="lastname"
          v-model="newGuests.lastname"
        required/><br />

        <label for="dish">Dish:</label><br />
        <select
          name="dish"
          id="dish"
          v-model="newGuests.dish"
        required>
          <option value="Soda">Soda</option>
          <option value="Nuggets">Nuggets</option>
          <option value="Cake">Cake</option>
          <option value="Hot dog">Hot dog</option>
        </select>
        <br /><br />
        <input type="button" value="Add" @click="addguest()"/>
      </form>
    </section>
  </main>
</template>

<script>
export default {
  name: "PeopleList",
  data() {
    return {
      guests: [
        {
          firstname: "Mary",
          lastname: "Johnson",
          dish: "Juice",
        },
      ],
      newGuests: {},
    };
  },
  methods: {
    addguest: function () {
        if (this.newGuests.firstname && this.newGuests.lastname && this.newGuests.dish){
            this.guests.push(this.newGuests);
           this.newGuests={};
        }else {
            alert("All fields must be filled");
        }
      
    },
  },
};
</script>








