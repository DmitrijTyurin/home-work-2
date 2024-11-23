<template>
   <li class="productData list">
        <div class="product sketchy">
          <span class="product-image"><img :src="productData.image" width="300" height="300" /></span>  
          <span class="product-data data">
            <div><span class="text">Наименование:</span> {{ productData.title }}</div>
            <div><span class="text">Цена:</span> {{ productData.price }}</div>
            <div><span class="text">Описание:</span> {{ productData.description }}</div>
            <div><span class="text">Категория:</span> {{ productData.category }}</div>
            <div><span class="text">Рейтинг:</span> {{ productData.rating.rate }}</div>
            <div><span class="text">Количество проголосовавших:</span> {{ productData.rating.count }}</div>
          </span>  
        </div>
      </li>
</template>

<script setup>
    defineProps(['productData'])
</script>

<style>
  .text {
    font-weight: 700;
    color: #987D93;
  }

  .list {
    margin-bottom: 40px;
    list-style: none;
  }

  .product {
    width: 90%;
    display: flex;
  }

  .product-image {
    float: left;
    width: 0%;
  }

  .product-data {
    margin-left: 35%;
    text-align: left;
    display:inline-block;
  }

  .sketchy {
      padding: 4rem 8rem;
      display: inline-block;
      border: 3px solid #333333;
      font-size: 1.0rem;
      border-radius: 2% 6% 5% 4% / 1% 1% 2% 4%;
      text-transform: uppercase;
      letter-spacing: 0.3ch;
      background: #ffffff;
      position: relative;
      
      &::before {
          content: '';
          border: 2px solid #353535;
          display: block;
          width: 100%;
          height: 100%;
          position: absolute;
          top: 50%;
          left: 50%;
          transform: translate3d(-50%, -50%, 0) scale(1.015) rotate(0.5deg);
          border-radius: 1% 1% 2% 4% / 2% 6% 5% 4%;
      }
  }

  .data{
    display:inline-block;
    width:60%;
    border-radius: 255px 15px 225px 15px/15px 225px 15px 255px;
    padding:1em;
    line-height:1.5em;
    background:hsla(67, 95%, 95%, 1);
    border:dotted 5px hsla(0, 95%, 35%, 1);
  }
</style>