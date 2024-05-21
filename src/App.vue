<template>
  <div>
    <Nav></Nav>
    <welcome></welcome>
    <jobs></jobs>
    <comments></comments>

  <siteFooter></siteFooter>
  </div>
</template>

<script>
import Modal from "./components/Modal.vue";
import Nav from "./components/Navigation.vue";
import welcome from "./components/welcome.vue";
import siteFooter from './components/siteFooter.vue';
import jobs from "./components/jobs.vue";
import comments from "./components/comments.vue";




export default {
  name: "App",
  components: { Modal, Nav, welcome, jobs, siteFooter,comments },
 /* data() {
    return {
      header: "Çekiliş için üye olun",
      text: "Yarı fiyatına almak için NFT alın",
      showModal: false,
      showModalTwo: false,
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.asd);
      this.$refs.classList.add("active");
      this.$refs.name.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    },
  },*/
};
</script>

<style>
#app,
.modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  
}
h1 {
 
  display: inline-block;
  padding-bottom: 10px;
}
html{
  overflow-x: hidden;
}

</style>
