<template>
  <div class="reviews">
    <div>
      Количество отзывов: {{count}}
    </div>
    <hr>
    <form id="reviewForm" v-on:submit.prevent="addNewReview">
      <div id="newReviewForm">
        <div class="newReviewFormItem">
          <input type = "text" placeholder = "Введите имя.." v-model="newReviewAuthor"/>
        </div>
        <div class="newReviewFormItem">
          <input type = "text" placeholder = "Оставьте отзыв.." v-model="newReview"/>
        </div>
        <div class="newReviewFormItem">
          <button type="submit" @click="increment">Отправить отзыв</button>
        </div>
      </div>
    </form>
    <hr>
    <ul id="reviewList">
      <li class = "reviewItem" v-for="(item, index) in reviews" :key="item.index">
        <div>
          Автор: {{ item.author }}
          <hr>
        </div>
          <div>
          {{ item.review }}
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
import store from '@/store'
export default{
  data: function() {
    return {
    newReview: '',
    newReviewAuthor: '',
    reviews: [
      { author: 'Ilya',
      review: 'Cool' },
      { author: 'Dima',
      review: 'Not Bad' }
    ]
  };
},
  computed: {
      count () {
  	    return store.state.count
      }
    },
    methods: {
      increment () {
        store.commit('increment')
      },
      addNewReview: function () {
      this.reviews.push({
        author: this.newReviewAuthor,
        review: this.newReview
      })
      this.newReview = '',
      this.newReviewAuthor = ''
    }
    }
}
</script>
<style scoped>
  #reviewList{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }
  .reviewItem{
    width: 400px;
    margin: 20px;
    padding: 10px;
    border: 2px solid #42b983;
    border-radius: 10px;
  }
  .newReviewFormItem{
    margin: 10px;
  }
  #newReviewForm{
    border: 1px solid black;
    border-radius: 10px;
  }
  #reviewForm{
    padding: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
