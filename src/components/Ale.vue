<template>
  <div class="book-of-memories">
    <div class="cover">
      <h1 class="title">Libro de Recuerdos</h1>
    </div>
    <div class="pages-container">
      <div class="page">
        <h2>Título de la Página</h2>
        <img src="imagen.jpg" alt="Página 1">
        <p>Descripción de la página.</p>
      </div>
      <div class="page">
        <h2>Título de la Página</h2>
        <img src="imagen.jpg" alt="Página 2">
        <p>Descripción de la página.</p>
      </div>
      <!-- Agrega más páginas según tus necesidades -->
    </div>
  </div>
</template>

<script>
export default {

}
  
</script>

<style scoped>
.book-of-memories {
  width: 600px;
  margin: 50px auto;
  background-color: #f5f5f5;
  border: 1px solid #ddd;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  padding: 20px;
  font-family: Arial, sans-serif;
}

.cover {
  background-image: url("");
  background-size: cover;
  background-position: center;
  width: 100%;
  height: 400px;
  margin-bottom: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.title {
  font-size: 36px;
  font-weight: bold;
  color: #fff;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
}

.pages-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.page {
  text-align: center;
  width: 200px;
  padding: 20px;
  margin: 10px;
  background-color: #fff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

h2 {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 10px;
}

img {
  width: 160px;
  height: auto;
  margin-bottom: 20px;
}

p {
  font-size: 16px;
  line-height: 1.5;
}


</style>
