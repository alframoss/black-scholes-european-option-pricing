# Black-Scholes European option pricing

This GitHub repository contains all the work related to my study of Black-Scholes European option pricing. My notes arise from my own independent research.

## Introduction

The Black-Scholes model is a model for the dynamics of a financial market containing derivative instruments. It is widely used in finance as one can deduce the Black-Scholes equation. This is a parabolic partial differential equation that has a closed form solution, which gives an estimate of the price of a European option. The main idea behind the model is to hedge the option by buying and selling the underlying asset in a way to eliminate risk. This type of hedging is called delta hedging.

## Assumptions

Under a continuous-time framework, investors are allowed to trade in the financial market up to finite time $T$. Let $(\Omega, \mathcal{F}, \mathbb{P})$ be a complete probability space and $(\mathcal F_t)_{0\leq t\leq T}$ be a right-continuous filtration containing all $\mathbb{P}$-null sets. In the financial market, there is a risky asset and a riskless asset. We make the following assumptions on the financial market.
- The price of the underlying risky asset follows a geometric Brownian motion

$$\text{d}S_t=\mu S_t\text{d}t+\sigma S_t\text{d}W_t,$$

- The price of the riskless asset follows the differential equation

$$\text{d}B_t=rB_t\text{d}t,$$

- The risk-free interest rate $r$ and volatility $\sigma$ are known functions,
- The asset pays no dividends during the life of the option,
- There are no transaction costs,
- There are no arbitrage opportunities within the market,
- The market is complete,
- Short selling is permitted.

## Problem Formulation

Let $V(S_t, t)$ denote the price of a derivative security, then $V(S_t, t)$ is governed by

$$\frac{\partial V}{\partial t}(S_t, t)+\frac{\sigma^2}{2}S_t^2\frac{\partial^2V}{\partial S_t^2}(S_t, t)+rS_t\frac{\partial V}{\partial S_t}(S_t, t)-rV(S_t, t)=0.$$

The price of a particular derivative can be obtained by setting suitable boundary conditions specific to the derivative. For example, a European call option has boundary condition $C(S_T, T)=\text{max}(S_T-K, 0)$. This equation can be derived using a riskless hedging portfolio argument as originally used by Black and Scholes.

## Closed Form Solution

A closed form solution can be derived using the heat equation. See Chapter 2.1 in `Black_Scholes_Project.pdf`. Wwe implement a heat map displaying the arbitrage price of call and put options using the closed form solution to the Black-Scholes equation for varying volatility and spot prices. In addition, given an arbitrary price of the underlying at expiration, we display a heat map displaying the profitability of call and put options. See the first part of `20062024_Black_Scholes_code.ipynb` for the implementation. 

## Risk-Neutral Pricing \& Monte Carlo Method

We also discuss the risk-neutral pricing approach which utilises a change of measure and the Monte Carlo method. This is discussed in great detail in Chapters 2.2-2.3 in `Black_Scholes_Project.pdf`.

## Results

To see both heat maps, check `Black_scholes_european_heatmap.png` and `Black_scholes_european_profitability_heatmap.png`. We analyse the convergence of Monte Carlo estimations. See `Black_scholes_MC_prices.png` and `Black_scholes_MC_errors.png`.

## Future Extensions

- Barrier options
- Greeks
- Psuedorandom and quasirandom sequeunces

