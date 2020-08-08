<template>
  <div>
    <Header />
    <main>
      <Nuxt />
    </main>
    <Footer />
  </div>
</template>

<script>
import Footer from "@/components/footer.vue";
import Header from "@/components/header.vue";
export default {
  components: {
    Header,
    Footer
  }
};
</script>

<style lang="scss" scoped>
	main {
		min-height: 400px;
		background-color: #fff;
		padding: 20px;
	}
	.page-enter-active,
	.page-leave-active {
		transition: 0.5s cubic-bezier(1, 0.25, 0.25, 1);
	}
	.page-enter,
	.page-leave-active {
		opacity: 0;
		transform: translate(0, 30px);
	}
</style>