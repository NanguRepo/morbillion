<script context="module">
	export const prerender = true;
</script>

<svelte:head>
	<title>Morbillion Converter</title>
</svelte:head>

<script>
	let x = 1, y = 128166873;
	let x2y = x => y = x * 128166873
	let y2x = y => x = y / 128166873
	$: x2y(x)
	$: y2x(y)
	const images = [
		"https://pbs.twimg.com/media/FQIPru8WYAM6sE-?format=jpg&name=medium",
		"https://pbs.twimg.com/media/FQHGeETXoAc_qMM?format=jpg&name=small",
		"https://pbs.twimg.com/media/FQFuo-UXoAosuuP?format=jpg&name=900x900",
		"https://pbs.twimg.com/media/FPliv2UXIAYXKrl?format=jpg&name=medium",
		"https://pbs.twimg.com/media/FP33xWKWUAAU48j?format=jpg&name=small",
		"https://pbs.twimg.com/media/FPlq1KZXEAMY1da?format=png&name=900x900",
		"https://pbs.twimg.com/media/FP4E4mPWYAsYWFj?format=jpg&name=medium",
		"https://pbs.twimg.com/media/FQEx3OBXEAAtdrU?format=jpg&name=medium",
		"https://pbs.twimg.com/media/FPrKZ30XoAwSmOb?format=jpg&name=medium"
	]
	let image = images[Math.floor(Math.random() * images.length)]
	let numberPicked
	function changeImage() {
		// create a function that returns a random number between two numbers
		let randomNumber = (min, max) => Math.floor(Math.random() * (max - min + 1)) + min
		numberPicked = randomNumber(1000, 5000)
		setTimeout(() => {
			image = images[Math.floor(Math.random() * images.length)]
			changeImage()
		}, numberPicked)
	}
	changeImage()
</script>

<body class="dark:bg-slate-800">
	<div class="h-screen w-screen dark:bg-slate-800 dark:text-white">
		<div class="bg-slate-200 shadow-lg rounded-lg px-4 py-4 w-fit h-fit m-auto mt-10 dark:bg-slate-700">
			<h1 class="text-5xl font-bold">Morbillion converter</h1>
			<div class="font-mono flex flex-col mt-10">
				<div class="flex flex-row justify-between items-center w-full">
					<h1>Morbillions</h1>
					<input class="numberInput" bind:value={x} type="number" />
				</div>
				<div class="flex flex-row justify-between items-center w-full">
					<h1>Dollars</h1>
					<input class="numberInput" bind:value={y} type="number" />
				</div>
			</div>
		</div>
		<img src={image} alt="morbius" class="rounded-lg lg:w-1/3 h-3/5 m-auto mt-10" />
		<h1 class="text-gray-400 dark:text-gray-500 text-center font-mono">{numberPicked}</h1>
	</div>
</body>