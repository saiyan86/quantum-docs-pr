---
# Mandatory fields. See more on aka.ms/skyeye/meta.
title: Intent and product brand in a unique string of 43-59 chars including spaces | Microsoft Docs 
description: 115-145 characters including spaces. Edit the intro para describing article intent to fit here. This abstract displays in the search result.
services: service-name-with-dashes-AZURE-ONLY 
keywords: Don’t add or edit keywords without consulting your SEO champ.
author: QuantumWriter
ms.author: MSFT-alias-person-or-DL
ms.date: 10/09/2017
ms.topic: article-type-from-white-list
# Use only one of the following. Use ms.service for services, ms.prod for on-prem. Remove the # before the relevant field.
# ms.service: service-name-from-white-list
# product-name-from-white-list

# Optional fields. Don't forget to remove # if you need a field.
# ms.custom: can-be-multiple-comma-separated
# ms.devlang:devlang-from-white-list
# ms.suite: 
# ms.tgt_pltfrm:
# ms.reviewer:
# manager: MSFT-alias-manager-or-PM-counterpart
---

# Advanced Matrix Concepts

We now extend our manipulation of Matrices to Eigenvalues, Eigenvectors and Exponentials which form a fundamental set of tools we need to describe and implement quantum algorithms.

## Eigenvalues and Eigenvectors

Let $M$ be a square matrix and $v$ be a vector that is not the all zeros vector (i.e., the vector with all entries equal to $0$).
Then we say $v$ is an eigenvector of  $M$ if $Mv = cv$ for some number $c$. We say $c$ is the eigenvalue corresponding to the eigenvector $v$. In general a matrix $M$ may transform a vector into any other vector, but an eigenvector is special because it is left unchanged except for being multiplied by a number. Note that if $v$ is an eigenvector with eigenvalue $c$, then $av$ is also an eigenvector (for any nonzero $a$) with the same eigenvlue. 

For example, for the identity matrix, every vector $v$ is an eigenvector with eigenvalue $1$. As another example, consider a diagonal matrix $D$ which only has nonzero entries on the diagonal:

$$
\begin{bmatrix}
	d_1 & 0 & 0 \\\\ 0 & d_2 & 0 \\\\ 0 & 0 & d_3
\end{bmatrix}
$$

The vectors 

$$\begin{bmatrix}1 \\\\ 0 \\\\ 0 \end{bmatrix}, \begin{bmatrix}0 \\\\ 1 \\\\ 0\end{bmatrix} and \begin{bmatrix}0 \\\\ 0 \\\\ 1\end{bmatrix}$$

are eigenvectors of this matrix with eigenvalues  $d_1$, $d_2$, and $d_3$ respectively. If $d_1$, $d_2$, and $d_3$ are distinct numbers, then these vectors (and their multiples) are the only eigenvectors of the matrix $D$. In general, for a diagonal matrix it is easy to read off the eigenvalues and eigenvectors. The eigenvalues are all the numbers appearing on the diagonal, and their respective eigenvectors are the unit vectors with one entry equal to $1$ and the remaining entries equal to $0$.

Note in the above example that the eigenvectors of $D$ formed a basis for $3$-dimensional vectors. A basis is a set of vectors such that any vector can be written as a linear combination of them. More explicitly, $v_1$, $v_2$, and $v_3$ form a basis if any vector $v$ can be written as $v=a_1 v_1 + a_2 v_2 + a_3 v_3$ for some numbers $a_1$, $a_2$, and $a_3$. 

For Hermitian and unitary matrices, which are  essentially the only matrices encountered in quantum computing, we have a general result known as the spectral theorem, which asserts the following: For any Hermitian or unitary matrix $M$, there exists a unitary $U$ such that $M=U^\dagger D U$ for some diagonal matrix $D$. Furthermore, the diagonal entries of $D$ will be the eigenvalues of $M$. We already know how to compute the eigenvalues and eigenvectors of a diagonal matrix $D$. Using this theorem we know that if $v$ is an eigenvector of $D$ with eigenvalue $c$, i.e., $Dv = cv$, then $U^\dagger v$ will be an eigenvector of $M$ with eigenvalue $c$. This is because 

$$M(U^\dagger v) = U^\dagger D U  (U^\dagger v) =U^\dagger D (U  U^\dagger) v = U^\dagger D v = c U^\dagger v$$

## Matrix Exponentials
A matrix exponential can also be defined in exact analogy to the exponential function.  The matrix exponential of a matrix $A$ can be expressed as

$$
e^A=\mathbb{1} + A + \frac{A^2}{2!}+\frac{A^3}{3!}+\cdots
$$
This is important to us because quantum mechanical time evolution is described by a unitary matrix of the form $e^{iB}$ for Hermitian matrix $B$.  For this reason, performing matrix exponentials is a fundamental part of quantum computing and as such Q# has intrinsic routines for describing these operations.
There are many ways in practice to compute a matrix exponential on a classical computer, and in general numerically approximating such an exponential it is fraught with peril.  See *Cleve Moler and Charles Van Loan. "Nineteen dubious ways to compute the exponential of a matrix." SIAM review 20.4 (1978): 801-836* for more information about the challenges involved.  

The easiest way to understand how to compute the exponential of a matrix is through the eigenvalues and eigenvectors of that matrix.  Specifically, the spectral theorem discussed above says that for every Hermitian or unitary matrix $A$ there exists a unitary matrix $U$ and a diagonal matrix $D$ such that $A=U^\dagger D U$.  Because of the properties of unitarity we have that $A^2 = U^\dagger D^2 U$ and similarly for any power $p$ $A^p = U^\dagger D^p U$.  If we substitute this into the operator definition of the operator exponential we obtain:

$$
e^A= U^\dagger \left(\mathbb{1} +D +\frac{D^2}{2!}+\cdots \right)U= U^\dagger \begin{bmatrix}\exp(D_{11}) & 0 &\cdots &0\\\\ 0 & \exp(D_{22})&\cdots& 0\\\\ \vdots &\vdots &\ddots &\vdots\\\\ 0&0&\cdots&\exp(D_{NN}) \end{bmatrix} U
$$

In other words, if you transform to the eigenbasis of the matrix $A$ then computing the matrix exponential is equivalent to computing the ordinary exponential of the eigenvalues of the matrix.  As many of the operations in quantum computing involve performing matrix exponentials, this trick of transforming into the eigenbasis of a matrix to simplify performing the operator exponential appears frequently and is the basis behind many quantum algorithms such as Trotter–Suzuki based quantum simulation methods.

Another useful property is if $B$ is both unitary and Hermitian, ie $B^2=\mathbb{1}$, then it can be seen by applying this rule to the above expansion of the operator exponential and grouping the $\mathbb{1}$ and the $B$ terms that for any real value $x$

$$e^{iBx}=\cos(x)\mathbb{1} + iB\sin(x)$$

This trick is especially useful because it allows us to reason about the actions that matrix exponentials have, even if the dimension of $B$ is exponentially large, for the special case when $B$ is both unitary and Hermitian. 