<template>
  <div class="home">
    <UserInfo/>
  </div>
</template>

<script>
// @ is an alias to /src
import UserInfo from "@/components/UserInfo"
export default {
  name: 'Home',
  components: {
    UserInfo
  }
}
</script>
