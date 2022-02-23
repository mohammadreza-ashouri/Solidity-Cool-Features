# Solidity-Cool-Features
Here in this page, I am introducing a couple of tips that allows Soldiity developers to optimize their code.


### Custom Errors in Solidity 0.8
Defining custom errors and use them with Revert, instead of String, reduces the gas consumption in the Solidity smart contracts.
Wht is like that?
If you use an string to show the error the amount of the gas depends on the string lenght. For example:


```
pragma solidity ^0.8;

contract Playground {
    address payable owner = payable(msg.sender);

    function withdraw() public {
        if (msg.sender != owner)
            revert(" This is a sample error string! You should not use it because it's costly!");

        owner.transfer(address(this).balance);
    }

}
````
 The execution cost of the withdraw function now is 23692 gas
