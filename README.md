# Reentrancy-attack
A replication of DAO Hack vulnerability

## Prerequisite
This code is integrated using **Remix Ethereum IDE**. To run this project, open Remix IDE in your web browser and create files to run the code.

## Overview
The infamous DAO hack was happened in 2016, a year after the launch of Ethereum. This hack was a result of **reentrancy attack**. `splitDAO` was the function prone to this attack.
This hack resulted in famous **hard fork** which led to Ethereum and Ethereum Classic. In this repo, I'll highlight the discrepancy and it's solution using the pattern of CHECK-EFFECT-INTERACTION.

## Step-by-Step Guide
1. Load the GitHub repo
2. Compile & Deploy FundRaiser
3. Compile & Deploy Attacker, with FundRaiser address as parameter
4. Set Value to 10000 and call `deposit` on Fundraiser. This will deposit money on YOUR balance
5. Call getTotalFunds on Fundraiser. Should show 10000.
6. Set Value to 400 and call `depositFunds` on Attacker. This will deposit money on the ATTACKER's balance
7. Call getTotalFunds on Fundraiser. Should show 10400.
8. Call getFunds on Attacker. Should show 0. The attacker has 0 funds currently.
9. Call withdrawFunds on Attacker. This is the attack.
10. Call getFunds on Attacker. Should show 1600 -- 4x what the Attacker deposited!
11. Delete both deployed contracts. Re-deploy both, but this time, build & deploy the UpdatedFundRaiser
12. Add funds to both, and try to drain via attack. The attack should fail.

## Disclaimer
Use this repo for the purpose of study.
