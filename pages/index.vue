<template>
  <div class="container row center">
    <div class="wrap">
      <div class="page-header">
        <h1>Hello.</h1>
        <div class="sub_header">
            My father just celebrated his 60th birthday! He'll appreciate any messages you'll written for him. Thanks!
        </div>
      </div>
      <div class="message-card-cntr col">
          <div class="header pull-apart row y-center">
              <div class="message-to">
                  <div>To</div>
                  <div>Paddy</div>
              </div>
              <div class="photo">
                <img src="~/assets/pp.png">
              </div>
          </div>
          <div class="textarea">
            <textarea id="message-area" rows="4" placeholder="Write a message here..." v-model="message" :disabled="sendingMessage">
            </textarea>
          </div>
          <div class="divider"></div>
          <div class="form-actions row pull-right">
            <button class="secondary-button btn"
              :disabled="sendingMessage"
              :class="{'btn-loading': this.sendingMessage}"
              @click="clearMessage"
              >
              Clear
            </button>
            <button class="cta-button btn"
              :disabled="sendingMessage"
              :class="{
                'btn-loading': this.sendingMessage,
                'btn-success': this.writeSuccessful && !this.writeError && !this.sendingMessage,
                'btn-error': !this.writeSuccessful && this.writeError && !this.sendingMessage,
              }"
              @click="addGreetings">
              {{ ctaButtonState }}
            </button>
          </div>
      </div>
      <div class="read-greetings">
        <button class="accent-button btn btn-full"
          @click="readMessages">
          Read all greetings
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import {fireDb} from '~/plugins/firebase.js'

export default {
  data() {
    return {
      writeSuccessful: false,
      writeError: false,
      sendingMessage: false,
      message: '',
      ctaButtonState: 'Send'
    }
  },
  methods: {
    clearMessage() {
      this.message = '';
    },
    readMessages() {
      this.$router.push({path: '/messages'});
    },
    async addGreetings() {
      let messageEl
      const ref = fireDb.collection("greetings").doc()
      const document = {
        message: this.message ?? 'Happy birthday Paddy! (auto-generated)',
        timestamp: Date.now(),
        author: null
      }

      this.sendingMessage = true;
      this.ctaButtonState = 'Loading...';
      try {
        return await ref.set(document)
          .then((res) => {
            this.sendingMessage = false
            this.writeSuccessful = true
            this.writeError = false
            this.ctaButtonState = 'Success!';
            this.message = '';
            setTimeout(() => {
              this.writeSuccessful = false;
              this.writeError = false;
              this.ctaButtonState = 'Send';
            }, 1500);
          });
      } catch (e) {
        this.sendingMessage = false
        this.writeError = true
        this.writeSuccessful = false
        this.ctaButtonState = 'Oops, please try again.';
        console.error(e)
        setTimeout(() => {
          this.writeSuccessful = false;
          this.writeError = false;
          this.ctaButtonState = 'Send';
        }, 3000);
      }
    }
  }
}
</script>

<style lang="scss">
$card-gutter: 1rem;

.read-greetings {
  margin-top: 3rem;
}

.wrap {
    padding: 2rem 1rem;
    max-width: 720px;
    width: 100%
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
  margin-bottom: 1.5rem;
  .photo {
      img {
        width: 3rem;
        height: 3rem;
      }
  }
}

#message-area {
  font-size: 20px;
  color: #333;
  font-weight: 500;
  width: 100%;
  font-family: 'Avenir', 'Roboto';
  border: none;
  &::placeholder { color: #bbb}
}

.form-actions {
  margin-top: $card-gutter;
  button + button{
    margin-left: $card-gutter;
  }
}

.divider {
  width: 100%;
  height: 1px;
  background-color: #EEEEEE;
}

.textarea {
  margin-bottom: $card-gutter;
}

</style>
