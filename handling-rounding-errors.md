## Handling Rounding Errors
JavaScript’s numbers are usually entered as decimal floating-point numbers, but they are internally represented as binary floating-point numbers. 
That leads to imprecision. To understand why, let’s forget JavaScript’s internal storage format and take a general look at what fractions can be well represented by decimal floating-point numbers and by binary floating-point numbers. In the decimal system, all fractions are a mantissa m divided by a power of 10: m / 10 e

Due to rounding errors, as a best practice you should not compare nonintegers directly. 
Instead, take an upper bound for rounding errors into consideration. 
Such an upper bound is called a machine epsilon. The standard epsilon value for double precision is 2^−53:
```
var EPSILON = Math.pow(2, -53);
function epsEqu(x, y) {
    return Math.abs(x - y) < EPSILON;
}
```
`epsEqu()` ensures correct results where a normal comparison would be inadequate:
```
> 0.1 + 0.2 === 0.3
false
> epsEqu(0.1+0.2, 0.3)
true
```
