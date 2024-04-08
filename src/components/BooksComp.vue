<script setup>
import {ref} from 'vue'

const books = ref([])
    
async function callApi() {
    const url = "http://localhost:3000/books"
    const fetcher = await fetch(url)
    const json = await fetcher.json()
    books.value = json
  
}
callApi()



</script>

<template>
    			<section id="main">
					<div class="container">

						<!-- Content -->
							<article class="box post">
								
								<header>
									<h2>Liste Books</h2>
									<p>Combien</p>
								</header>
								<p>
									<table>
										<tr>
										  <th>Titre</th>
										  <th>Auteur</th>
										  <th>Type</th>
										  <th>Action</th>
										</tr>
										<tr v-for="book in books" >
										  <td>{{book.title}}</td>
										  <td> {{ book.author.firstName }} {{ book.author.lastName }}</td>
										  <td> {{ book.genre }}</td>
										  <td><button>voir</button></td>
                                        </tr>
									  </table>
								</p>
								
							</article>

					</div>
				</section>
</template>