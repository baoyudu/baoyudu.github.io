---
layout: single
title: Understand the concept of Filtration
date: 2023-06-05 16:41
tags: [Stochastic Process]
math: true
---

# Definition

> A filtration on $(\Omega, \mathcal{A}, \mathbb{P})$ is an increasing sequence $\left(\mathcal{F}_n\right)_{n \in \mathbb{Z}_{+}}$of sub- $\sigma$-fields of $\mathcal{A}$. We have thus
> $$
> \mathcal{F}_0 \subset \mathcal{F}_1 \subset \mathcal{F}_2 \subset \cdots \subset \mathcal{A}
> $$
{:.def}

We also say that $\left(\Omega, \mathcal{A},\left(\mathcal{F}_n\right)_{n \in \mathbb{Z}_{+}}, \mathbb{P}\right)$ is a filtered probability space.
The parameter $n \in \mathbb{Z}_{+}$is usually interpreted as time. The $\sigma$-field $\mathcal{F}_n$ gathers the information available at time $n$ (events that are $\mathcal{F}_n$-measurable are interpreted as those that depend only on what has happened up to time $n$ ). We will write
$$
\mathcal{F}_{\infty}=\bigvee_{n \in \mathbb{Z}_{+}} \mathcal{F}_n:=\sigma\left(\bigcup_{n \in \mathbb{Z}_{+}} \mathcal{F}_n\right)
$$
# Examples
(a) If $\left(X_n\right)_{n \in \mathbb{Z}_{+}}$is a random process, then, for every $n \in \mathbb{Z}_{+}$, we may define $\mathcal{F}_n^X$ as the smallest $\sigma$-field on $\Omega$ for which $X_0, X_1, \ldots, X_n$ are measurable:
$$
\mathcal{F}_n^X=\sigma\left(X_0, X_1, \ldots, X_n\right) .
$$
Then $\left(\mathcal{F}_n^X\right)_{n \in \mathbb{Z}_{+}}$is a filtration called the canonical filtration of $\left(X_n\right)_{n \in \mathbb{Z}_{+}}$.
(b) Suppose that $\Omega=[0,1), \mathcal{A}$ is the Borel $\sigma$-field on $[0,1)$, and $\mathbb{P}$ is Lebesgue measure. For every $n \in \mathbb{Z}_{+}$, set
$$
\mathcal{F}_n=\sigma\left(\left[\frac{i-1}{2^n}, \frac{i}{2^n}\right) ; i \in\left\{1,2, \ldots, 2^n\right\}\right) .
$$
Then $\left(\mathcal{F}_n\right)_{n \in \mathbb{Z}_{+}}$is a filtration called the dyadic filtration on $[0,1)$.

# Understanding
The $\sigma$-algebra $\mathcal{F}_t$ represents all the events that we can "know" or "measure" at time $t$. Here's a way to think about this.

Consider a simple example. Suppose we are observing the weather each day. We might have a stochastic process $\{X_t\}$ where $X_t$ represents the weather (say, temperature) at day $t$.

Now, at any given day $t$, what do we know? Well, we certainly know the weather from all previous days - those are past events that we've observed. And we know the weather today. But we do not know the weather on future days.

So, the $\sigma$-algebra $\mathcal{F}_t$ includes all the events that involve the weather up to and including day $t$. If $E$ is an event in $\mathcal{F}_t$, that means $E$ is a set of outcomes that we can determine whether or not has occurred based on the weather up to day $t$. For example, the event "It was hotter than 80 degrees on day 3" is in $\mathcal{F}_t$ for any $t \geq 3$.

That's why $\mathcal{F}_t$ is interpreted as "the information available at time $t$". **It includes all the events that we can know whether they have happened or not based on what we've observed up to time $t$.**

To help understand this concept, let's look at a specific example:

Suppose we have a fair coin, where $X_n$ represents the result of the $n^{th}$ toss, and $F_1$ and $F_2$ are the sigma-algebras corresponding to the information we obtain after the first and second tosses, respectively.

We label the outcomes as "H" for heads (or 1) and "T" for tails (0).

Then, $\mathcal{F}_1$ would contain all events that can be determined from the first toss. Specifically, they can be enumerated as:

- $\{\Phi\}$: The empty set, corresponding to an event with no outcome (an impossible event).
- $\{H\}$: The event where the first toss results in heads.
- $\{T\}$: The event where the first toss results in tails.
- $\{H, T\}$: The entire sample space, corresponding to a certain event.

Similarly, $\mathcal{F}_2$ would contain all events that can be determined from the first two tosses. It can be enumerated as:

- $\{\Phi\}$: The empty set.
- $\{HH\}$: The event where two consecutive tosses are heads.
- $\{HT\}$: The event where the first toss is heads and the second is tails.
- $\{TH\}$: The event where the first toss is tails and the second is heads.
- $\{TT\}$: The event where two consecutive tosses are tails.
- $\{HH, HT\}$: The event where the first toss results in heads (regardless of the second toss's outcome).
- $\{TH, TT\}$: The event where the first toss results in tails (regardless of the second toss's outcome).
- $\{HH, TH\}$: The event where the second toss results in heads (regardless of the first toss's outcome).
- $\{HT, TT\}$: The event where the second toss results in tails (regardless of the first toss's outcome).
- $\{HH, HT, TH, TT\}$: The entire sample space.

The role of a $\sigma$-algebra in this context is to formalize the idea of "events" or "outcomes" that we can measure or know. It is a mathematical tool that lets us handle the concept of information in a precise way. 

This understanding also leads to the idea of a process being adapted to a filtration. 


> A stochastic process $\{X_t\}$ is adapted to a filtration $\{\mathcal{F}_t\}$ if the value $X_t$ at each time $t$ is a function of the information available at that time, i.e., is $\mathcal{F}_t$-measurable. 
{:.def}

This means that, for each $t$, the value $X_t$ can be determined based on the information available up to and including time $t$.


