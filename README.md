# KSTest
 
The package provides 3 functions, one to perform the Kolmogorov-Smirnov test
one to calculate Kolmogorov D statistic and one to compute D p-value.

Kolmogorov-Smirnov is a nonparametric test to test the hypothesis that the
sample is extracted from a given continue distribution.
The algorithm used in the package is the same as that described in "A
Procedure to Find Exact Critical Values of Kolmogorov-Smirnov Test.",
Facchinetti, S. (2009).

PUBLIC FUNCTION:
--------------------------------------------------------------
### Function:	KSTest(series s, string d, matrix pars, scalar alpha[0:1:0.05])

Description:	Prints Kolmogorov Dn statistic for the sample s, its p-value
		and the critical value D for a given alpha.

Arguments:	Series s, sample to test.
		String d, is the same value as "d" parameter in gretl function
		"cdf". The accepted functions are:
			- Standard normal (d = z, n, or N)
			- Logistic (lgt or s): no extra arguments
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
		Matrix pars, contains the values passed to cdf for the choosen
		distribution fuction.
		Scalar alpha, (optional) value on which the critical value D
		is calculated.

Output:		The function returns nothing.



### Function:	D_pval(scalar n, scalar D)

Description:	Calcualte p-value of D using Facchinetti's algorithm.

Arguments:	Scalar n, observations in the sample.
		Scalar D, Kolmogorov statistic.

Output:		Scalar p-value.



### Function:	D(scalar alpha, scalar n)

Description:	Inverse of function D_pval. Iteratively run D_pval to find
		critical value given alpa and n.

Arguments:	Scalar alpha, p-value of D searched
		Scalar n, observations in the sample.

Output:		Scalar D, critic value.
