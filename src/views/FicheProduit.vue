<template>
    <div>
        <h1>Détails produit</h1>

    
    <div v-if="prodSelect" class="detailsProd detailsFlex">
        
        <div class="detailsLeft">
            <div class="details_img">
                <img :src="prodSelect.image" alt="Produit sélectionné">
            </div>
        </div>
        
        <div class="detailsRight">
            <h2>{{ prodSelect.titre }}</h2>
            <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Facere dolorum laborum molestiae maiores iste non veniam error qui. Laudantium eligendi iusto, illo accusamus assumenda molestiae veritatis adipisci quibusdam sed voluptatem.</p>
            <p>MOQ : {{ prodSelect.moq }}</p>
            <div v-if="online">
            <p class="price">{{ prodSelect.prix }}</p>
            <button @click="add(prodSelect)">Ajouter au panier</button>
            </div>
        </div>
        
   
    </div>

    </div>
  </template>
  
  <script>
import { mapState } from 'vuex';
  export default {

    data() {
        return {
            prodSelect: null,
        };
    },

    computed: {
        ...mapState(['produits', 'online'],)
    },

    created() {
        if(this.$route.params.productId) {
            this.prodSelect = this.$store.getters.getProduitById(parseInt(this.$route.params.productId));
            console.log('Produit sélectionné :', this.prodSelect);
        }
    },

    methods: {

    }

  }
  </script>
  
  <style scoped>
*, ::before, ::after{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}
h1{
    margin-top: 180px;
}

.detailsProd{
    max-width: 75%;
    margin: auto;
    height: auto;
    background-color:#cca88c;
    margin-top: 10px;
    box-shadow: 5px 5px 10px 3px rgba(0, 0, 0, 0.3);
}

.detailsLeft,.detailsRight {
    width: 50%;
    padding: 30px;
}

.detailsFlex{
    display: flex;
    justify-content: space-between;
}

.details_img{
    width: auto;
    height: auto;
}

.detailsRight{
    padding: 50px 100px 50px 100px;

}

h1,h2{
    color: #472e16;
    font-size: 25px;
    
}

p{
    color: #5e3c1a;
    margin: 20px 0 30px 0;
    line-height: 25px;
}

.price{
    color: #472e16;
}


button {
    background-color: #b98d68;
    color: #5e3c1a;
    border: none;
    border-radius: 5px;
    margin-top: 20px;
    margin-bottom: 15px;
    padding: 5px;
    width: 150px;
    height: 40px;
    border-radius: 20px;
    border: 1px solid #5e3c1a;
    cursor: pointer;
    font-weight: bold;
}

button:hover {
background-color: #5e3c1a;
color: #cca88c;
}
  </style>