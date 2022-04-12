<script context="module">
	export const prerender = true;
</script>

<svelte:head>
	<title>Morbillion Converter</title>
</svelte:head>

<script>
	let x = 1, y = 126377221;
	let x2y = x => y = x * 126377221
	let y2x = y => x = y / 126377221
	$: x2y(x)
	$: y2x(y)
	const randomMorbiusImage = () => {
		const images = [
			"https://pbs.twimg.com/media/FQIPru8WYAM6sE-?format=jpg&name=medium",
			"https://pbs.twimg.com/media/FQHGeETXoAc_qMM?format=jpg&name=small",
			"https://pbs.twimg.com/media/FQFuo-UXoAosuuP?format=jpg&name=900x900",
			"https://pbs.twimg.com/media/FPliv2UXIAYXKrl?format=jpg&name=medium",
			"https://pbs.twimg.com/media/FP33xWKWUAAU48j?format=jpg&name=small",
			"https://pbs.twimg.com/media/FPlq1KZXEAMY1da?format=png&name=900x900",
			"https://pbs.twimg.com/media/FP4E4mPWYAsYWFj?format=jpg&name=medium",
			"https://pbs.twimg.com/media/FQEx3OBXEAAtdrU?format=jpg&name=medium",
			"https://pbs.twimg.com/media/FPrKZ30XoAwSmOb?format=jpg&name=medium",
			""
		]
		return images[Math.floor(Math.random() * images.length)]
	}
</script>

<body class="dark:bg-gray-800">
	<div class="h-screen w-screen dark:bg-gray-800 dark:text-white">
		<div class="bg-slate-200 shadow-lg rounded px-4 py-4 w-fit h-fit m-auto mt-10 dark:bg-gray-700">
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
		<img src={randomMorbiusImage()} alt="morbius" class="rounded lg:w-1/3 h-3/5 m-auto mt-10" />
	</div>
</body>