<template>
  <div class="container">
    <div class="wrap">
      <div class="page-header">
        <h1>Hello.</h1>
        <div class="sub_header">
            My father just celebrated his 60th birthday! He'll appreciate any messages you'll written for him. Thanks!
        </div>
      </div>
      <div class="message-card-cntr">
          <div class="header pull-apart row y-center">
              <div class="message-to">
                  <div>To</div>
                  <div>Paddy</div>
              </div>
              <div class="photo"></div>
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
    padding: 1rem;
    box-shadow: 1px 3px 24px -3px rgba(0,0,0,.5);
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
    .photo {
        width: 3rem;
        height: 3rem;
        border-radius: 50%;
        background-color: #777;
    }
}
</style>
