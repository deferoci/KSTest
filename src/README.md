# Introduction

The package provides 3 functions, one to perform the Kolmogorov-Smirnov test one to compute Kolmogorov D statistic and one to compute D p-value.

Kolmogorov-Smirnov is a nonparametric test to test the hypothesis that the sample is extracted from a given continuous distribution.

The algorithm used in the package is the same as that described in "A Procedure to Find Exact Critical Values of Kolmogorov-Smirnov Test.", Facchinetti, S. (2009).

Source code can also be found here: https://github.com/deferoci/KSTest


# Public function

```
KSTest(series s, string d, matrix pars[null], scalar alpha[0:1:0.05], bool verbose)
```

Prints the Kolmogorov `Dn` statistic for the series `s`, its p-value and the critical value `D` for a given `alpha`.

## Arguments

- `s`, series, Series to be tested
- `d`, string, The same value as the "d" parameter as for gretl's built-in function `cdf()`. The accepted functions are:
	- Standard normal (d = z, n, or N)
	- Logistic (lgt or s)
	- Student's t (t)
	- Chi square (c, x, or X)
	- Snedecor's F (f or F)
	- Gamma (g or G)
	- Beta (beta)
	- Exponential (exp)
	- Weibull (w or W)
	- Laplace (l or L)
	- Generalized Error (E)
	- Non-central chi square (ncX)
	- Non-central F (ncF)
	- Non-central t (nct)
	- Uniform (u or U) NOTE This function is not accepted in `cdf()`. Takes 2 parameters as input, `a` (left endpoint of support) and `b` (right endpoint)

- `pars`, matrix (optional), contains the values passed to `cdf()` for the chosen distribution function. If the distribution function requires no parameters can be omitted.
- `alpha`, scalar (optional, default 0.05), value for which the critical value `D` is computed.
- `verbose`, bool (optional, default 1), set 0 to not print output.

## Output

Return the vector `{Dn, p-value, D}`


```
D_pval(scalar n, scalar D)
```

Calculate p-value of `D` using Facchinetti's algorithm.

## Arguments

- `n`, scalar, Number of observations in the sample.
- `D`, scalar, Kolmogorov statistic.

## Output

Scalar p-value.



```
D(scalar alpha, scalar n)
```

Inverse of function `D_pval()`. Iteratively run `D_pval()` to find critical value given `alpa` and `n`.

## Arguments

- `alpha`, scalar, p-value of `D` searched
- `n`, scalar, Number of observations

## Output

Scalar `D`, the critical value.


# Changelog

* **v1.0 (May 2023)**
  * Initial release
