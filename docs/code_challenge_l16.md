# **Libraries**

## **Overview**
Using libraries is a common day task while programming. We often follow the DRY (Do not repeat yourself principle) and that involves using as much as possible from what is already implemented. In this code challenge, you excersice those skills while working on a data analytics app for a business.

---

## **Learning Goals**
By the end of this lab, you will be able to:

✅ Create your own Makefile
✅ Use external libraries to build a CLI based interface

---

## **Part 0: Description of the App**
You are going to work on a Data Analytics app for a retail store. The app is going to read a file and perform some computations/analysis based on the input.

1. Download the dataset from https://archive.ics.uci.edu/dataset/352/online+retail
2. Fist analysis: Find the number of transactions per country. If there is no input from the CLI provide the counter for all countries. If the user passes one parameter as a input, show the number of transactions for that country.
3. Second analysis: Calculate the total amount of the transactions. There should be a CLI parameter `--only-uk`that if given calculates all the transactions for the UK. Otherwise, the calculations is done for all the records.

## **Part 1: Create a CLI App**
### ✅ **Task 1.1 Create a parser for the arguments**

1. Parse input parameter using the library CLI11 (https://github.com/CLIUtils/CLI11)
2. Test your application with serveral input parameters from the terminal


### ✅ **Task 1.2 Create a progress bar for your application**
1. Create a progress bar for your application using the barkeep library (https://github.com/oir/barkeep). The progress bar can show the progress of reading the file, the calculations, or both.
2. Test the correct behaviour of the progress bar, you can test multiple versions of the progress bar.

## **Part 2: Create a Makefile**
### ✅ **Task 2.1 Makefile**
1. Create the appropiate Makefile for your project
2. Compile using the `make` command