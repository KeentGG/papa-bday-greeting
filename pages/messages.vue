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
                  <div>From</div>
                  <div>Anonymous</div>
              </div>
              <div class="photo">
                <img src="~/assets/pp.png">
              </div>
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

.divider {
  width: 100%;
  height: 1px;
  background-color: #EEEEEE;
}


</style>
