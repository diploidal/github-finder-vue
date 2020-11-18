<template>
  <div class="search-container d-grid">
    <h1 class="mb-5">{{ instruction }}</h1>
    <form @submit.prevent="handleRequest(name)">
      <input
        v-model="name"
        type="text" 
        className="form-control" 
        placeholder="Github Username" 
        aria-label="Username" 
        aria-describedby="basic-addon1"
      />
      <div class="d-grid">
        <code class="mt-2">{{name}}</code>
        <button type="submit" class="btn btn-primary mt-4">
          Search
        </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  props: {
    instruction: String
  },
  data () {
    return {
      name: '',
      userInformation: {},
      userRepositories: {},
      requestInformation: {},
      isRequestReceived: false
    }
  },
  methods: {
    async handleRequest(name) {
      const API_LINK = `https://api.github.com/users`;
      const response = await fetch(`${API_LINK}/${name}`)
          if(!response.ok) {
      this.requestInformation = response;
      this.isRequestReceived = false;
    } else {
      response.json().then((data) => {
        this.userInformation = data
        this.requestInformation = response; //TODO: investigate why response cant assign properly here
        this.isRequestReceived = true;
        })
        const repoResponse = await fetch(`${API_LINK}/${name}/repos`);
          repoResponse.json().then((data) => {
          this.userRepositories = data
        })
      }
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.search-container {
  padding: 6rem 0px;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  text-align: center;
}
form {
  justify-self: center;
}
</style>
