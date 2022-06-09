<style>
	
	#main-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

#center-content {
  /* Lets middle column shrink/grow to available width */
  flex: 1 1 auto;
	min-width: 100px;
}

#left-content{
  /* Forces side columns to stay same width */
  flex: 0 0 200px;
}

#right-content {
  /* Forces side columns to stay same width */
  flex: 0 0 300px;
}
	
</style>

<script>
	// default
	let number=13;
	let result=true;
	let displayResult="true";
	
	// select
	let selected=1;
	let selection = [
		{ id: 1, text: `isPrime`},
		{ id: 2, text: `isFibonacci` },
		];
	
	var action = () => {		
	  number = Math.round( number );	
		number = (number < 0) ? 1 : number;
		let result = (selected === 1) ? isPrime(number) : isFibonacci(number);
		displayResult = result ? "true" : "false";
	}
	
  var isPrime = (n) => {
		for(var i = 2; i < n; i++)
			if(n % i === 0) return false;
		return n > 1;
	}
	
	var isFibonacci = (n) => {
    if (isSquare(5*(n*n)-4) || isSquare(5*(n*n)+4)) {
       return true;
    } else { return false; }
	}
	
	// fibonacci
	
	var isPerfectSquare = (n) => {

    let s = parseInt(Math.sqrt(n));
    return (s * s == n);
	}
	
	var isFibonacci = (n) => {

    return isPerfectSquare(5 * n * n + 4) ||
           isPerfectSquare(5 * n * n - 4);
	}
	
  // Fibonacci code is contributed by Rajput-Ji

	
</script>


<div id="main-container">
  <div id="left-content">
		<input
		type=number
		bind:value={number}
		style="width:100px;"
		on:change={ () =>  action() }
		>
  </div>

  <div id="center-content">
		<select bind:value={selected} on:change="{() =>  action()}">
			{#each selection as select}
				<option value={select.id}>
					{select.text}
				</option>
			{/each}
		</select>
  </div>

  <div id="right-content">
    <div id="result">
			{displayResult}
		</div>

  </div>
</div>

