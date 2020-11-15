<template>
  <div class="search-container d-grid">
    <h1 class="mb-5">{{ instruction }}</h1>
    <form>
      <input 
        type="text" 
        className="form-control" 
        placeholder="Github Username" 
        aria-label="Username" 
        aria-describedby="basic-addon1"
        value=""
      />
      <div class="d-grid">
        <button type="submit" class="btn btn-primary mt-4">
          Search
        </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'Header',
  props: {
    instruction: String
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
