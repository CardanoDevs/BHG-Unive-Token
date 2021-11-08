1. Name:UNIVE  
2. Symbol: UNV
3. Supply: 100M
4. Décimal: 8
5. Max tx per transaction:50K
6. Buy tax: 5% for liquidity, 10% for holders / total 15%
7. Sell tax:5% for liquidity, 15% for holders / total 20%
8. Owner: 0x1c4bF8D7F124b32934a0959460F19acEe106d757


-Reward dispensed hourly if gas is sufficient. (btc, eth, bnb usdt)

-Reward for all holders who have at least 20 tokens.

# Help

BSC distributioncontract :  https://bscscan.com/address/0x24938a81d8b3c6544869b293b997b77bf3e22a8d#contracts
BSC Scooby               :  https://bscscan.com/address/0xf0ab4b8daa51f6abf6b4c9fef0cca5d127029aa9#code
Scooby.finance url       :  https://www.scooby.finance/




1. change address to deploy owner address. in SBD.sol 

Line 979 -980
   address payable distribute=0x2Ab7f9F7fc2a02CFeA25E3F4c83336A907Bc3B92;
     bool public setContractAddy = false;
      function distributeAdd(address payable _distribute) public onlyOwner(){
        require(distribute==0x2Ab7f9F7fc2a02CFeA25E3F4c83336A907Bc3B92, 'Distribute Contract can be set once only');
            distribute = _distribute;
    }

2. deploy SBD token solidity and copy token's address,

3. In distribution.sol add tokenaddress and owneraddress  
    line 230,231
    IERC20 public Scooby = IERC20("TOKEN'S ADDRESS");
    address payable wallet = Owner address;
    
Please add the token's address.

4. Deploy "distribution.sol" and copy "distribution.sol" address

5. execute "distributionAdd" in token's contract with distribution contract's address

6. add liquidity.

7. there is happens token transfer between holders ...
........................... 
As a result 1. Token contract get some BNB balance
            2. happens Add liquidity 
	    3. increase every holder's reward balance (please check "myRewards" variable)

===========================================================================================================================================================

claimRewards

1. execute setSwapAndLiquifyEnabled function to swap liquidity.


2. in the distribution contract, get data that every holder's reward balance from the token contract.
	first,  get the holder's number "tokenholders" variable in the distribution contract.
	second, set Loop variable as 0, number of token holders "setloop".
	execute "distribute" function to get the reward balance of every holder.
        execute "transferToDistribute" in token contract(SBD.sol),  then bnb balance of token contract move to distribution contract.
        check  holder's reward balance in distribution contract "myrewards"

3. set setSwapAndLiquifyEnabled function to disable swap liquidity function.

4. claimRewards.





