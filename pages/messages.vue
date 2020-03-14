<template>
  <div class="container">
    <div class="wrap">
      <div class="page-header">
        <h1>Thank you all.</h1>
        <div class="sub_header">
            My father just celebrated his 60th birthday! He'll appreciate any messages you'll written for him. Thanks!
        </div>
      </div>
      <div v-for="(message, index) in messages" :key=index>
        <div class="message-card-cntr col">
          <div class="header pull-apart y-center">
            <div class="message-to">
              <div>From</div>
              <div>{{message.author || 'Anonymous'}}</div>
            </div>
          </div>
          <div class="message">
            {{message.message}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import {fireDb} from '~/plugins/firebase.js'

export default {
  mounted() {
    try {
      const ref = fireDb.collection("greetings").get().then(querySnapshot => {
        querySnapshot.forEach(doc => {
          this.messages.push(doc.data());
        });
      });
    } catch (e) {
      console.error(e)
    }
  },
  data() {
    return {
      messages: []
    }
  },
  methods: {
    async readFromFirestore() {

    }
  },
  computed: {
    getMessages() {
      let greetings = [];

      // return new Promise((resolve, reject) => {

      // });
      try {
        const ref = fireDb.collection("greetings").get().then(querySnapshot => {
          querySnapshot.forEach(doc => {
            this.messages.push(doc.data());
          });
        });
      } catch (e) {
        // TODO: error handling
        console.error(e)
      }

    }
  }
}
</script>

<style lang="scss" scoped>
$card-gutter: 1rem;

.wrap {
    padding: 2rem 1rem;
}
.sub_header {
    font-size: 20px;
    font-weight: 500;
    color: #666;
}
.message-card-cntr {
    border-radius: 13px;
    background-color: white;
    padding: $card-gutter;
    box-shadow: 1px 4px 20px -4px rgba(0,0,0,.25);
    margin-bottom: 1rem;
}
.message-to {
    font-size: 24px;
    font-weight: 700;
    div {
        display: block;
        line-height: 1.15em;
        &:first-child {
            color: #CFCFCF;
        }
        &:last-child {
            color: #A1A1A1;
        }
    }
}

.page-header {
  margin-bottom: 2rem;
}

.header {
  margin-bottom: 1rem;
  .photo {
      img {
        width: 3rem;
        height: 3rem;
      }
  }
}

.divider {
  width: 100%;
  height: 1px;
  background-color: #EEEEEE;
}

.message {
  font-size: 18px;
  font-weight: 500;
  color: #333;
}

li {
  list-style: none;
}


</style>
