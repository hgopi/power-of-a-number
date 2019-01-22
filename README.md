# power-of-a-number
Find the power of the given base to the exponent without using native methods like math.pow

The `Math.pow()` function returns the `base` to the `exponent` power, that is, `base<sup>exponent</sup>`.

Create a function to replicate the behavior of that native method to find the exponent value of the given number.
```
function toPower(x, n) {
	if (n < 0) return toPower(1 / x, -n);
	else if (n === 0) return 1;
	else if (n === 1) return x;
	else if (n % 2 === 0) return toPower(x * x, n / 2);
	else if (n % 2 !== 0) return x * toPower(x * x, (n - 1) / 2);
}
console.log(toPower(2, 3)); // 8
console.log(toPower(10, 2)); // 100
```
Without recursion:
```
function toPowerWithoutRecursion(x, n) {
	if (n < 0) {
		x = 1 / x;
		n = -n;
	}

	if (n === 0) return 1;
	let y = 1;

	while (n > 1) {
		if (n % 2 === 0) {
			x = x * x;
			n = n / 2;
		} else {
			y = x * y;
			x = x * x;
			n = (n - 1) / 2;
		}
	}
	return x * y;
}
console.log(toPowerWithoutRecursion(2, 6)); // 8
console.log(toPowerWithoutRecursion(10, 2)); // 100
```
