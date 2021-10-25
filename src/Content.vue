<template>
  <main>
    <Header
      :totalPrices="totalPricePurchases"
      :totalPurchased="totalArticlesPurchased"
    ></Header>
    <div id="all-products-container">
      <div id="product-container" v-for="(product, index) in products" :key="index">
        <Product
            @update-qty="updateQty"
            :productName=product.name
            :productDescription=product.desc
            :productPrice=product.price
            :imgSrc=product.source
            :imgAlt=product.alt
            :number=product.num
            :cheap=isCheapest(product)
            :expensive=isExpensive(product)
        >
        </Product>
      </div>
    </div>
  </main>
</template>

<script>

import Header from "./components/Header.vue"
import Product from "./components/Product.vue"

export default {
  name: "Content",
  components: {
    Product,
    Header
  },
  data: () => {
    return {
      totalPricePurchases: 0,
      totalArticlesPurchased: 0,
      products: {
        football: {
          id: 0,
          name: "Football",
          source: "https://upload.wikimedia.org/wikipedia/commons/thumb/6/6e/Football_%28soccer_ball%29.svg/1200px-Football_%28soccer_ball%29.svg.png",
          alt: "A football",
          desc: "To play football",
          price: 20,
          num: 12
        },
        beer: {
          id: 1,
          name: "Hikari Beer",
          source: "https://cdn.store-factory.com/www.satsuki.fr/content/product_9584993b.jpg?v=1532683523",
          alt: "A Beer",
          desc: "Blond Beer 5°",
          price: 7.50,
          num: 8
        },
        senators: {
          id: 2,
          name: "The Senators ! Apolitique",
          source: "https://i1.sndcdn.com/artworks-NbZ8tm41qG5cz5t5-aySMJQ-t500x500.jpg",
          alt: "The debut album of the best punk band in France",
          desc: "The debut album of the best punk band in France",
          price: 10,
          num: 20
        },
        frite: {
          id: 3,
          name: "Frite",
          source: "https://gourmandiz.dhnet.be/app/uploads/2019/03/frites6-4096x2918.jpg",
          alt: "A frite",
          desc: "The frite of Nico",
          price: 5.50,
          num: 12
        },
        frite1: {
          id: 4,
          name: "Nike Air",
          source: "https://www.kindpng.com/picc/m/29-291720_nike-roshe-run-monogram-transparent-background-nike-shoes.png",
          alt: "Nike Air",
          desc: "Be the prettiest and the most hype person",
          price: 300,
          num: 30
        },
        nicolas: {
          id: 5,
          name: "Nicolas Montero--Fraysse",
          source: "https://media-exp1.licdn.com/dms/image/C4E03AQEWJRhXf70MhQ/profile-displayphoto-shrink_200_200/0/1617311305559?e=1637193600&v=beta&t=qDU38jeOlgHaFhb-0eRu4EZr2vzhkRkkciyW2VvDvkA",
          alt: "Nicoco",
          desc: "My roomate, please buy him",
          price: 20,
          num: 15
        },
        arthur: {
          id: 6,
          name: "Arthur Nguyen",
          source: "https://media-exp1.licdn.com/dms/image/C4D03AQF_7qgt7Vt4Yg/profile-displayphoto-shrink_800_800/0/1596565291019?e=1640822400&v=beta&t=bLO4VW7HKxP_ZOM3teIMX6AlaVb6y5SQCSjph3ZKMD4",
          alt: "Arthur",
          desc: "The Architect, the prettiest man // human in the universe",
          price: 10000,
          num: 1
        },
        wiktor: {
          id: 7,
          name: "Wiktor Wielgos",
          source: "https://media-exp1.licdn.com/dms/image/C4E03AQGrWIyTu9onkg/profile-displayphoto-shrink_800_800/0/1581407444860?e=1640217600&v=beta&t=4UVEKh5AI_kajIv4v0wkRWEHjTBPneMwH5uIgduTorU",
          alt: "Wiktor",
          desc: "The prettiest man on earth (After Arthur)",
          price: 1,
          num: 23
        },
      }
    }
  },
  methods : {
    isCheapest(el) {
      return !Object.entries(this.products).some(entrie => entrie[1].price < el.price)
    },
    isExpensive(el) {
      return !Object.entries(this.products).some(entrie => entrie[1].price > el.price)
    },
    updateQty(qty, value) {
      this.totalArticlesPurchased+=qty
      this.totalPricePurchases+=value

      console.log(this.totalArticlesPurchased + " " + this.totalPricePurchases)
    }
  }
}
</script>

<style scoped>

* {
  border: 0;
  padding: 0;
}

main {
  height: auto;
  margin-top: 80px;

  display: flex;
  flex-direction: column;
}

#all-products-container {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  flex-wrap: wrap;
  height: 100%;

  margin-top: 10px;
}

</style>