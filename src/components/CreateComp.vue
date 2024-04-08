<script setup>
    import {ref} from 'vue'
    import HeaderComp from './HeaderComp.vue';
    import FormComp from './FormComp.vue';

    const firstName = ref('')
    const lastName = ref('')
    const title = ref('')
    const originalTitle = ref('')
    const publicationYear = ref('')
    const genre = ref('')
    const coverUri = ref('')
    const recap = ref('')








async function pushApi(){

    const formData = {
        author: {
            firstName:firstName.value,
            lastName: lastName.value
        },
        title: title.value,
        originalTitle: originalTitle.value,
        publicationYear: parseInt(publicationYear.value),
        genre: genre.value,
        coverUri: coverUri.value,
        recap: recap.value
    };
    console.log(formData)

const reponse = await fetch("http://localhost:3000/books", {
      method: "POST", // ou 'PUT'
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(formData),
    });

}

function isFormValid() {
        return firstName.value && lastName.value && title.value && originalTitle.value && publicationYear.value && genre.value && coverUri.value && recap.value;
    }
   

  

</script>

<template>

<div id="page-wrapper">

			<!-- Header -->

			<!-- Main -->
				<section id="main">
					<div class="container">

						<!-- Content -->

						<h2> Create/ Update Form</h2>


						<p>
                            <form>
								<div class="row gtr-50">
									<div class="col-12 col-12-small">
										<input name="firstName" placeholder="firstName" type="text" v-model="firstName">
									</div>
									<div class="col-12 col-12-small">
										<input name="lastName" placeholder="lastName" type="text" v-model="lastName">
									</div>
									<div class="col-12 col-12-small">
										<input name="title" placeholder="title" type="text" v-model="title">
									</div>
									<div class="col-12 col-12-small">
										<input name="originalTitle" placeholder="originalTitle" type="text" v-model="originalTitle">
									</div>
									<div class="col-12 col-12-small">
										<input name="publicationYear" placeholder="publicationYear" type="text" v-model="publicationYear">
									</div>
									<div class="col-12 col-12-small">
										<input name="genre" placeholder="genre" type="text" v-model="genre">
									</div>
									<div class="col-12 col-12-small">
										<input name="coverUri" placeholder="coverUri" type="text" v-model="coverUri">
									</div>
									<div class="col-12 col-12-small">
										<input name="recap" placeholder="recap" type="text" v-model="recap">
									</div> 
                                    <div class="col-12">
										<button type="button" @click="pushApi" class="form-button-submit button icon solid fa-pen " :disabled="!isFormValid()">Create</button>
									</div>
								</div>
                               
							</form>

                            
						</p>
								


					</div>
				</section>

			
		</div>
        
    </template>