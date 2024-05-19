# Smart Contract
This Solidity program is a "Money Lending" smart contract. This program uses the assert(), revert(), and require() statements.

## Description
This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain.

## Getting Started
### How to run this program?
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., Loan.sol). Copy and paste the following code into the file:


**
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.25;

contract getLoan {
    address public lender;
    uint256 public loanAmount;
    bool public isLoanGiven;

    constructor() {
        lender = msg.sender;
    }

    function loanMoney(uint256 amount) public {
        require(msg.sender == lender, "Only lender can call this function.");
        require(!isLoanGiven, "Loan has already been given.");
        require(amount > 0, "Enter the amount of money you will loan.");
        
        loanAmount = amount;
        isLoanGiven = true;
    }

    function payDebt(uint256 paymentAmount) public payable {
    require(isLoanGiven, "No loan has been given yet");
    require(paymentAmount > 0 && paymentAmount <= loanAmount, "Payment amount exceeds loan amount");

    assert(paymentAmount <= loanAmount);

    loanAmount -= paymentAmount;
    isLoanGiven = false;
    }

    function cancelLoan() public {
    require(isLoanGiven, "No loan has been given yet");

    isLoanGiven = false;
    loanAmount = 0;

    revert("Loan has been cancelled.");
    }
  }


To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.25" (or another compatible version), and then click on the "Compile Loan.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "HelloWorld" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling the loanMoney, payDebt, cancelLoan, isLoanGiven, lender, loanAmount functions.


## Author
Daniel Burgos


## License
This project is licensed under the MIT License - see the LICENSE.md file for details



