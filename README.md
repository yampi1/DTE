# dte

Address: 0xFd2407D2A34a5CC0F8ea2962DEf3c9A520B66840

DTE stands for Decentralized Token Exchange and it is an ethereum smart contract.
It has 1% fee for the order taker, the fee is distributed between the contract's share holders by its shares token.
New tokens to be traded can be added for a fee of 100 finneys which again goes to the shareholders.
The shares can be bought and sold on DTE and when the shares are put up in a sell order, the contract address will receive no part of the fee revenue.
To put up a new order the function newOrder() is used.
It takes 5 arguments; bool isSellOrder, uint soldTokenNo, uint boughtTokenNo, uint256 soldAmount, uint256 boughtAmount.
isSellOrder is set to true if it is a sell order.
soldTokenNo is the number of the token to be sold on the DTE. (number 0 is ethereum and number 1 is the shares token, token number 0 can not be used while isSellOrder is set to true for this argument)
boughtTokenNo is the number of the token on the DTE that is wanted.
soldAmount is the total amount of the tokens to be sold.
boughtAmount is the total amount of the tokens that is wanted.
Price calculation has to be done on the web3 front end. (which I can't make btw)

To take or partially fill an order the function takeOrder() is used.
It takes 3 arguments; bool isSellOrder, uint orderNo, uint256 amount.
isSellOrder specifies whether or not the order to be taken or filled partially is a sell order (when true) or not.
orderNo is the number of the actual order.
amount is the amount of the token you are willing to fill of the order.
You have to allow DTE 101% of the amount or send 101% of the ether to cover for the 1% taker fee.

When you put up an order, you have to allow the token you are selling to take the amount you are willing to sell from the token adminpage into itself.

When you want to cancel an order you put up the function cancelOrder() is used.
It takes 2 arguments; bool isSellOrder, uint orderNo
If your order has been partially filled already, you are only refunded the remaining amount.

to add a new token the function addToken() is used and it has a single argument and that is the address of the token to be added.

the function DistributeDividends() takes one argument and that is the token number of the tokens it has gained as fees.
If the amount amount of total fees collected divided by the total shares is less than 1 wei then the function will throw.
If the function successfully executes, each address that held shares of DTE before and during the function call will receive their share and have to call the function claimDividendShare() with the argument of the token number that they wish to withdraw to receive their share from DTE.
