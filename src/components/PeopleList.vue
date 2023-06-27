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
        <input class='button' type="button" value="Add" @click="addguest()"/>
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

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@200;300;400;500;700&family=Roboto:wght@100;300;400;500;700;900&family=Source+Sans+Pro:wght@200;300;400;600;700;900&display=swap");

body {
  width: 100vw;
  height: 100vh;
  align-items: center;
  justify-content: center;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
  background-color: rgba(255, 200, 221, 0.553);
  background-image: url('https://media1.giphy.com/media/WNJATm9pwnjpjI1i0g/giphy.webp?cid=ecf05e47hhyb6fpmdnm8lbgc5yvtpaxc4noua2dtbhg7lxt5&ep=v1_gif_associations&rid=giphy.webp&ct=s');
}

main {
  text-align: center;
  padding: 45px;
}

main table {
  margin: auto;
  font-size: 14px;
}

main td,
main th {
  padding: 8px;
  border-collapse: collapse;
  
}

main th {
  border-bottom: 1px solid rgb(255, 255, 255);
}

main p {
  margin-top: 0px;
}

main form input,
main form select {
  height: 24px;
  width: 240px;
  box-sizing: border-box;
}

main form label {
  font-size: 12px;
}

section.add-more {
  background-color: rgb(205, 180, 219);
  padding: 40px;
  margin-top: 40px;
  margin-left: 400px;
  margin-right: 400px;
  border-radius: 5%;
}

.button {
  background-color: rgb(189, 224, 254);
  border: solid;
  border-color: rgb(189, 224, 254);
  border-radius: 5px;
  transition-duration: 0.4s;
  color: black;
  padding: 15px 32px;
  text-align: center;
  font-size: 13px;
  margin: 4px 4px;
  cursor: pointer;
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.1), 0 6px 20px 0 rgba(0,0,0,0.1);
} 

.button:hover {
  background-color: rgb(162, 210, 255);
  border-color: rgb(162, 210, 255);
  box-shadow: 0 12px 16px 0 rgba(0,0,0,0.14), 0 17px 50px 0 rgba(0,0,0,0.0.9);
}
</style>