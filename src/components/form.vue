<template>
  <div>
    <form>
      <div v-if="step === 1">
        <h1>Step One</h1>
        <p>
          <legend for="name">Your Name:</legend>
          <input id="name" name="name" v-model="registration.name" />
        </p>

        <p>
          <legend for="email">Your Email:</legend>
          <input
            id="email"
            name="email"
            type="email"
            v-model="registration.email"
          />
        </p>

        <button @click.prevent="next()">Next</button>
      </div>

      <div v-if="step === 2">
        <h1>Step Two</h1>
        <p>How many do you want?</p>
        <br />
        <input
          type="radio"
          id="one"
          value="1"
          v-model="registration.qPicked"
          name="qPicked"
        />
        <label for="one">One</label>
        <br />
        <input
          type="radio"
          id="two"
          value="2"
          v-model="registration.qPicked"
          name="qPicked"
        />
        <label for="two">Two</label>
        <br />
        <input
          type="radio"
          id="three"
          value="3"
          v-model="registration.qPicked"
          name="qPicked"
        />
        <label for="three">Three</label>
        <br />

        <button @click.prevent="prev()">Previous</button>
        <button @click.prevent="next()">Next</button>
      </div>

      <div v-if="step === 3">
        <h1>Step Three</h1>

        You get 1! You did not skip a step

        <button @click.prevent="prev()">Previous</button>
        <button @click.prevent="next()">Next</button>
      </div>

      <div v-if="step === 4">
        <h1>Step Four</h1>

        You get 2! You skipped 1 step.

        <button @click.prevent="prev()">Previous</button>
        <button @click.prevent="next()">Next</button>
      </div>

      <div v-if="step === 5">
        <h1>Step Three</h1>

        You get 3! You skipped 2 steps.

        <button @click.prevent="prev()">Previous</button>
        <button @click.prevent="next()">Next</button>
      </div>

      <div v-if="step === 6">
        <h1>Step Three</h1>

        Confirm submission!

        <button @click.prevent="prev()">Previous</button>
        <button @click.prevent="submit()">Next</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  el: "#app",
  data() {
    return {
      step: 1,
      registration: {
        name: null,
        email: null,
        qPicked: null,
      },
    };
  },
  methods: {
    prev() {
      if (this.step > 2 && this.step <= 6) {
        this.step = 2;
      } else {
        this.step--;
      }
    },
    next() {
      if (this.step === 2 && this.registration.qPicked === "1") {
        this.step++;
      } else if (this.step === 2 && this.registration.qPicked === "2") {
        this.step += 2;
      } else if (this.step === 2 && this.registration.qPicked === "3") {
        this.step += 3;
      } else if (this.step > 2 && this.registration.qPicked !== "NULL") {
        this.step = 6;
      } else {
        this.step++;
      }
    },
    submit() {
      alert("Submit to blah and show blah and etc.");
    },
  },
};
</script>