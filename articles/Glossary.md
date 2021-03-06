---
# Mandatory fields. See more on aka.ms/skyeye/meta.
title: Glossary | Microsoft Docs 
description: Quantum terms glossary
author: QuantumWriter
ms.author: Alan.Geller@microsoft.com 
ms.date: 12/11/2017
ms.topic: article
# Use only one of the following. Use ms.service for services, ms.prod for on-prem. Remove the # before the relevant field.
# For Quantum products none of these categories have been defined  yet.
# ms.service: service-name-from-white-list
# ms.prod: product-name-from-white-list
# ms.technology: tech-name-from-white-list
---

|Term|Definition|
|-------------|----------|
|Adjoint|The complex conjugate transpose of the operation. For operations that implement a unitary operator, the adjoint is the inverse of the operation.|
|Callable|Operations and functions are collectively known as *callables*.|
|Canon|Operations and functions defined in Q# building on the logic defined in the prelude. The canon implementation is agnostic with respect to target machines.|
|Clifford group|The set of operations that occupy the octants of the Bloch sphere. These include: `X`, `Y`, `Z`, `H` and `S`|
|Controlled|A quantum operation that takes one or more qubits as enablers for the target operation.|
|Dirac Notation|A shorthand representation of quantum state. See the [Dirac Notation](quantum-concepts-6-DiracNotation.md) section for more details.|
|Eigenvalues and Eigenvectors|See the [Advanced Matrix section](quantum-concepts-3-MatrixAdvanced.md) for details.|
|EPR pair|Also known as a [Bell State](https://en.wikipedia.org/wiki/Bell_state)|
|Evolution|How the state changes over time. See the section on <xref:microsoft.quantum.concepts.matrix-advanced#matrix-exponentials> for an example. |
|Function|Purely classical routines in the Q# language|
|Measurement|Obtaining a classical bit from a qubit (or set of qubits). See the [Qubit Concepts](quantum-concepts-4-Qubit.md) section for more details.|
|Mutable|A variable whose value may be changed after it is created.|
|Namespace|A label for a collection of related names (typically operations, functions, and types). For instance the namespace `Microsoft.Quantum.Canon` labels all of the symbols defined by [the canon](xref:microsoft.quantum.canon).|
|Operation|The basic unit of quantum execution in Q#. It is roughly equivalent to a function in C or C++ or Python, or a static method in C# or Java.|
|Operator Application|Performing a quantum operation. This typically applies a unitary matrix to the current state vector. See [Introduction to Quantum Concepts](quantum-concepts-1-Intro.md) for more detail.|
|Oracle|A subroutine that provides data-dependent information to a quantum algorithm at runtime. Typically, the goal is to provide a superposition of outputs corresponding to inputs that are in superposition.   |
|Partial Application|Calling a function or operation without all the required parameters. The returns a new callable that only needs the missing parameters supplied during a future application.|
|Pauli Operators|The `X`, `Y` and `Z` quantum gates.|
|Prelude|The set of primitive and classical operations and functions defined by each individual target machine, rather than at the Q# level.|
|Quantum Circuit|The representation of a program for a quantum computer. See the <xref:microsoft.quantum.concepts.circuits> section for more details.|
|Quantum State|A representation of the qubits in the system. This is usually denoted as a complex column vector. For more information, see <xref:microsoft.quantum.concepts.vectors>. |
|Qubit|Unit of quantum storage. See the <xref:microsoft.quantum.concepts.qubit> section for more details.|
|Repeat-until-success|A quantum algorithm that probabilistically succeeds. Upon failure, the routine will re-try until successful (or a limit has been reached). |
|Software Stack|The complete set of classical and quantum software as well as the compilers, simulators and runtimes necessary to operate a quantum computer. See the <xref:microsoft.quantum.concepts.software-stack> section for more details. |
|Target machine|A compilation target that lowers an abstract quantum program towards hardware or simulation. This typically include re-writes for many purposes including gate replacement, encoding for error correction, geometric layout and others.|
|Tuple|Comma separated types grouped together via parenthesis. |
|User-defined type|Collection of built-in or previously defined types that may be referred to as a single unit.|

