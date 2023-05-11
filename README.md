The package provides 3 functions, one to perform the Kolmogorov-Smirnov test
one to compute Kolmogorov D statistic and one to compute D p-value.

Kolmogorov-Smirnov is a nonparametric test to test the hypothesis that the
sample is extracted from a given continuous distribution.
The algorithm used in the package is the same as that described in "A
Procedure to Find Exact Critical Values of Kolmogorov-Smirnov Test.",
Facchinetti, S. (2009).

Source code can also be found here:
https://github.com/deferoci/KSTest

FUNCTIONS:
===============================================================================
Function:	KSTest(series s, string d, matrix pars,
		       scalar alpha[0:1:0.05], bool verbose)

Description:	Prints Kolmogorov Dn statistic for the sample s, its p-value
		and the critical value D for a given alpha. Return the vector
		{Dn, p-value, D}

Arguments:	Series s, sample to test.
		String d, is the same value as "d" parameter in gretl function
		"cdf". The accepted functions are:
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
			- Uniform (u or U) NOTE This function is not accepted
			  in "cdf". Takes 2 parameters as input, a (left
			  endpoint of support) and b (right endpoint)
		Matrix pars, contains the values passed to cdf for the chosen
		distribution fuction.
		Scalar alpha (optional, default 0.05), value for which the
		critical value D is computed.
		Bool verbose (optional, default 1), set 0 to not print output.

Output:		Return the vector {Dn, p-value, D}

-------------------------------------------------------------------------------

Function:	D_pval(scalar n, scalar D)

Description:	Calcualte p-value of D using Facchinetti's algorithm.

Arguments:	Scalar n, observations in the sample.
		Scalar D, Kolmogorov statistic.

Output:		Scalar p-value.

-------------------------------------------------------------------------------

Function:	D(scalar alpha, scalar n)

Description:	Inverse of function D_pval. Iteratively run D_pval to find
		critical value given alpa and n.

Arguments:	Scalar alpha, p-value of D searched
		Scalar n, observations in the sample.

Output:		Scalar D, critical value.
