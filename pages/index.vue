<template>
  <div class="container">
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
            <textarea id="message-area" rows="4" placeholder="Happy birthday Paddy...">
            </textarea>
          </div>
          <div class="divider"></div>
          <div class="form-actions row pull-right">
            <button class="secondary-button btn">
              Cancel
            </button>
            <button class="cta-button btn">
              Send
            </button>
          </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {

}
</script>

<style lang="scss">
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
  font-weight: 400;
  width: 100%;
  font-family: 'Avenir';
}

.btn {
  font-size: 17px;
  font-weight: 700;
  border-radius: 9px;
  padding: 9px 19px;
  border: none;
  &.cta-button {
    background-color: #5D9CEC;
    color: white;
  }
  &.secondary-button {
    background-color: #F5F5F5;
    color: #999;
  }
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
