<script>
	import { Carousel } from 'flowbite-svelte';
	import images from './images.json';
</script>

<div class="w-screen">
	<Carousel {images} duration="3000" />
</div>
