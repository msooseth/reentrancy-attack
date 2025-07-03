# Reentrancy-attack
A replication of DAO Hack vulnerability

## Prerequisite
This code is integrated using **Remix Ethereum IDE**. To run this project, open Remix IDE in your web browser and create files to run the code.

## Overview
The infamous DAO hack was happened in 2016, a year after the launch of Ethereum. This hack was a result of **reentrancy attack**. `splitDAO` was the function prone to this attack.
This hack resulted in famous **hard fork** which led to Ethereum and Ethereum Classic. In this repo, I'll highlight the discrepancy and it's solution using the pattern of CHECK-EFFECT-INTERACTION.

## Step-by-Step Guide
1. Load the GitHub repo
2. Compile
3. Deploy FundRaiser
4. Deploy Attacker, with FundRaiser address as parameter
5. Set Value to 10000 and call `deposit` on Fundraiser. This will deposit money on YOUR balance
6. Call getTotalFunds on Fundraiser. Should show 10000.
7. Set Value to 400 and call `depositFunds` on Attacker. This will deposit money on the ATTACKER's balance
8. Call getTotalFunds on Fundraiser. Should show 10400.
9. Call getFunds on Attacker. Should show 0. The attacker has 0 funds currently.
10. Call withdrawFunds on Attacker. This is the attack.
11. Call getFunds on Attacker. Should show 1600 -- 4x what the Attacker deposited!

## Disclaimer
Use this repo for the purpose of study.
