<template>
  <main>
    <Header></Header>
    <div id="all-products-container">
      <div id="product-container" v-for="product in products" :key="product">
        <Product
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
      products: {
        football: {
          name: "Football",
          source: "https://upload.wikimedia.org/wikipedia/commons/thumb/6/6e/Football_%28soccer_ball%29.svg/1200px-Football_%28soccer_ball%29.svg.png",
          alt: "A football",
          desc: "To play football",
          price: 20,
          num: 12
        },
        beer: {
          name: "Hikari Beer",
          source: "https://cdn.store-factory.com/www.satsuki.fr/content/product_9584993b.jpg?v=1532683523",
          alt: "A Beer",
          desc: "Blond Beer 5°",
          price: 7.50,
          num: 8
        },
        senators: {
          name: "The Senators ! Apolitique",
          source: "https://i1.sndcdn.com/artworks-NbZ8tm41qG5cz5t5-aySMJQ-t500x500.jpg",
          alt: "The debut album of the best punk band in France",
          desc: "The debut album of the best punk band in France",
          price: 10,
          num: 20
        },
        frite: {
          name: "Frite",
          source: "https://gourmandiz.dhnet.be/app/uploads/2019/03/frites6-4096x2918.jpg",
          alt: "A frite",
          desc: "The frite of Nico",
          price: 5.50,
          num: 12
        },
        frite1: {
          name: "Nike Air",
          source: "https://www.kindpng.com/picc/m/29-291720_nike-roshe-run-monogram-transparent-background-nike-shoes.png",
          alt: "Nike Air",
          desc: "Be the prettiest and the most hype person",
          price: 300,
          num: 30
        },
        frite2: {
          name: "Frite",
          source: "https://gourmandiz.dhnet.be/app/uploads/2019/03/frites6-4096x2918.jpg",
          alt: "A frite",
          desc: "The frite of Nico",
          price: 20,
          num: 15
        },
        frite3: {
          name: "Frite",
          source: "https://gourmandiz.dhnet.be/app/uploads/2019/03/frites6-4096x2918.jpg",
          alt: "A frite",
          desc: "The frite of Nico",
          price: 20,
          num: 50
        },
        frite4: {
          name: "Frite",
          source: "https://gourmandiz.dhnet.be/app/uploads/2019/03/frites6-4096x2918.jpg",
          alt: "A frite",
          desc: "The frite of Nico",
          price: 20,
          num: 23
        }
      }
    }
  },
  methods : {
    isCheapest(el) {
      return !Object.entries(this.products).some(entrie => entrie[1].price < el.price)
    },
    isExpensive(el) {
      return !Object.entries(this.products).some(entrie => entrie[1].price > el.price)
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