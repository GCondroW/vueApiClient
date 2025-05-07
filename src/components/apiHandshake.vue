<script setup>
	const apiUrl="https://account.accurate.id/oauth/authorize";
	const urlParams = {
		client_id:"ad3864c1-16bb-4551-922b-8721c6c5a438",
		response_type:"code",
		scope:"item_view ",
		redirect_uri:"http://api-test123.test"
	};

	let getUrl=(apiUrl,urlParams)=>{
		const urlObj = new URL(apiUrl);
		Object.keys(urlParams).map(x=>{
			urlObj.searchParams.append(x,urlParams[x]);
		})
		return urlObj;
	};

	
	const getData = (urlObj) => {
		fetch(urlObj, {
			headers: { 'Content-type': 'application/json' },
		}).then(res=>res.json()).then((response) => {
			console.log({ response })
		}).catch((error) => {
			console.log('Looks like there was a problem: \n', error);
		});
	}

	getData(getUrl(apiUrl,urlParams));
</script>