# Kek Baggies Memecoin Mutual Fund

The Kek Baggies Memecoin Mutual Fund is a smart contract operating as a pooled investment fund for a basket of memecoins and other tokens on the Base chain.
Our goal is to seek returns by providing exposure to the memecoin market while reducing overall risk through diversification.
The fund provides to investors a convenient way to invest in memecoins without having to put in the effort of manually managing their own crypto portfolio.

The mutual fund is deployed entirely on-chain, enabling us to operate with much greater transparency and decentralization than investors would be
able to experience with a traditional mutual fund.

This README is intended to serve as a complete documentation of the mutual fund contract and the web interface for interacting with it. This is
a living document which will be updated for completeness and clarification as necessary.

If you have any questions or concerns, please join us on [Telegram](https://t.me/KekBaggiesToken).

## Contents
* [Quickstart](#quickstart)
    * [Buying Shares](#buying-shares)
    * [Selling Shares](#selling-shares)
* [Mutual Fund Structure](#mutual-fund-structure)
    * [Contract](#contract)
    * [Portfolio Management](#portfolio-management)
    * [Shares](#shares)
    * [Minimum Deposit](#minimum-deposit)
    * [Disabling Deposits](#disabling-deposits)
    * [Fees](#fees)
    * [Slippage](#slippage)
* [Reserve Token](#reserve-token)
* [Contract Addresses](#contract-addresses)
* [Disclaimer](#disclaimer)

## Quickstart
If you are not interested in reading about all of the details of the internal workings of the fund, this section provides
a quick guide on how to use the web interface to buy and sell shares.

![Main fund web interface](images/fund-main.png)

1. Install the MetaMask browser extension and use it to create a new Web3 wallet.
2. Buy some ETH on the Base chain, or bridge ETH from another chain to Base.
3. Use your Base ETH to buy our reserve token [$KEKBGS on Uniswap](https://app.uniswap.org/swap?outputCurrency=0xe7A704EAA3232756C8504FCF01Dcb535dc2df2A2&chain=base).
4. **(Optional)** Add $KEKBGS to your MetaMask wallet by importing the contract address `0xe7A704EAA3232756C8504FCF01Dcb535dc2df2A2`.
5. Visit https://kekbaggi.es/fund/ to access the fund's web interface.
6. The website will prompt you to connect to the Base chain if you do not currently have it selected in your wallet. Click the `Switch to Base Chain` button and allow the Base chain to be added to your list of networks if necessary. Then allow your active chain to be switched to Base. Upon switching your selected chain, the page will refresh.
7. The website will then prompt you to connect a wallet. Click the `Connect Wallet` button and select the account that has your $KEKBGS tokens. The page will refresh again upon selecting a new account.

### Buying Shares
Now that you have $KEKBGS on Base and have connected your wallet to the fund's web interface, you can buy shares of the Kek Baggies Memecoin Mutual Fund.

![Fund deposit modal](images/fund-deposit-modal.png)

1. In the `Manage Account` section of the web interface, click the `Buy Shares` button.
2. In the modal that appears, you can view your current share balance as well as the amount of $KEKBGS available for buying shares in your wallet.
3. Enter a deposit amount of $KEKBGS in the input field. We will subtract the deposit fee and then divide the
remainder by the current share price to determine how many shares to buy. The final purchase quantity is displayed in the modal.
4. Click `Approve Tokens` and then confirm the transaction in your wallet. Approving the tokens will allow the fund contract to spend your tokens on portfolio assets on your behalf.
5. Wait a few moments for the approval transaction to be confirmed.
6. Once your token allowace is updated, the `Approve Tokens` button will change to say `Buy Shares`.
7. Click `Buy Shares` and then confirm the transaction in your wallet.
8. Wait a few moments for the share purchase transaction to be confirmed.
9. Once the purchase transaction is confirmed, the page will refresh. Don't panic if the page doesn't update to show your new share balance right away.
Due to latency in the Base RPC provider, you may need to refresh the page a few times before your new share balance and equity are shown correctly.
10. You are now a shareholder in the Kek Baggies Memecoin Mutual Fund!
11. **(Optional)** Add the share token $KBMFST to your MetaMask wallet by importing the contract address `0xa34A1adDE2dDDfB1FB54024285daB566E755e188`.
This will enable you to view your share balance directly in your wallet or transfer the share tokens to another account.

**SHARES CAN ONLY BE BOUGHT FROM THE FUND BY USING THE WEB INTERFACE.**

**DO NOT SEND $KEKBGS OR OTHER ASSETS DIRECTLY TO THE FUND'S CONTRACT ADDRESS. NO SHARES WILL BE ISSUED TO YOU IF YOU DO THIS.**

**ONLY USE THE SHARE PURCHASE PROCEDURE OUTLINED IN THIS DOCUMENT. WE WILL NOT BE ABLE TO HELP YOU RECOVER YOUR ASSETS IF YOU JUST SEND THEM TO THE FUND'S CONTRACT ADDRESS.**

### Selling Shares

Now that you are holding share tokens, you can sell your shares back to the fund at the current share price at any time.

![Fund withdraw modal](images/fund-withdraw-modal.png)

1. In the `Manage Account` section of the web interface, click the `Sell Shares` button.
2. In the modal that appears, you can view your current share balance as well as the current share price.
3. Enter the amount of shares you wish to sell in the `Sell Quantity` field.
4. Paste the Base wallet address to which you wish to send proceeds from the share sale in the `To Address` field.
5. The `Estimated Proceeds` display will update to show an estimate of the total amount of $KEKBGS tokens you will receive in exchange for your shares. Due to slippage during asset liquidation, the actual $KEKBGS tokens you receive may be slightly less than the displayed estimate.
6. **Double check to verify that you have entered the correct address. We cannot help you recover funds if you send them to the wrong address.**
7. Click `Sell Shares` and confirm the transaction in your wallet.
8. Once the transaction is confirmed, the page will refresh. Don't panic if the page doesn't update to show your new share balance right away.
Due to latency in the Base RPC provider, you may need to refresh the page a few times before your new share balance and equity are shown correctly.

**SHARES CAN ONLY BE SOLD TO THE FUND BY USING THE WEB INTERFACE.**

**DO NOT SEND SHARE TOKENS DIRECTLY TO THE FUND'S CONTRACT ADDRESS. YOUR SHARES WILL BE LOST IF YOU DO THIS.**

**ONLY USE THE SHARE SALE PROCEDURE OUTLINED IN THIS DOCUMENT. WE WILL NOT BE ABLE TO HELP YOU RECOVER YOUR SHARES IF YOU JUST SEND THEM TO THE FUND'S CONTRACT ADDRESS.**
## Mutual Fund Structure
The fund is structured similarly to a traditional open-ended mutual fund where shares are able to be purchased from and sold back to the fund at the current share price at any time.
Investors can use our reserve token $KEKBGS to purchase shares directly from the fund.
See the [Shares](#shares) subsection for more information.

### Contract
The source code of the mutual fund contract is available in this repository and is verified on [BaseScan]().

The contract is responsible for maintaining custody over user deposits, as well as the buying/selling of portfolio assets with funds deposited by users. The contract has full
custody over these assets and manages them as specified in the contract code. Devs are not able to sell or transfer portfolio assets out of the fund. Investors are always
entitled to receive the full value (less slippage) of their asset entitlement by selling their shares back to the fund at the current share price.

When a user deposits KEKBGS into the fund by calling `deposit(uint256 amount)`, the fund contract transfers `amount` KEKBGS from the user's wallet to the fund's contract address.
The contract then calculates the total number of purchased shares by dividing the deposited amount of KEKBGS by the current share price. The contract only sells whole shares,
so we only transfer the total value of the whole number of shares purchased minus their "change".
The contract then uses deposited KEKBGS to purchase portfolio assets. Finally, the fund contract mints to the user's wallet the previously-calculated quantity of share tokens.

When a user sells shares back to the fund by calling `withdraw(uint256 shares, address to)`, the fund sells portions of the fund's portfolio assets for KEKBGS and transfers
the proceeds to the address specified by `to`. The calling account must have at least the number of share tokens specified by the `shares` argument. For each token in the
fund's portfolio, the sale quantity is calculated by `shares * token.balanceOf(address(this)) / sharesOutstanding` where `address(this)` is the address of the mutual fund
contract. We then transfer the user's reserve token entitlement to the address specified by `to` by calculating `shares * getReserveTokenBalance() / sharesOutstanding`.
Finally, the contract burns from the user's wallet the number of shares they sold back to the fund.

These buying/selling operations should typically be performed in the web UI as documented above. Only advanced users should interact with the smart contract functions directly.
Please contact us on Telegram if you need help with this.

For this first version of the mutual fund contract, the fund is only able to buy and sell assets that are exchanged on Uniswap V2. Future versions of this mutual fund
may have support for more exchange protocols, but we decided to keep the initial version simple by only supporting one exchange protocol.

There are a few additional read-only contract functions that would be useful to document here:
* `getNetAssetValue()` returns the total value of all assets held by the fund contract in KEKBGS, minus the current deposit fee balance.
* `getReserveTokenBalance()` returns the total quantity of reserve tokens currently held by the fund minus the current deposit fee balance.
* `getPortfolio()` returns information about the fund's asset holdings, including contract addresses, portfolio allocation basis points, token symbols,
token balances, and token balance value in KEKBGS for each asset in the fund's portfolio.

There are also a number of additional self-explanatory getters and setters that can be inspected by reading the contract source code. Please contact us on Telegram
if you need help understanding any part of the source code.

### Portfolio Management

### Shares
Users are able to buy shares from and sell shares to the mutual fund contract at the current share price. The share price is calculated as `getNetAssetValue() / getSharesOutstanding()` where `NetAssetValue`
is the total value of the fund's assets in KEKBGS minus the current deposit fee balance. `SharesOutstanding` is the total count of shares that are currently held by investors.

Shares in the fund are issued as standard ERC20 tokens. When a user buys shares, the fund contract mints to their wallet a quantity of share tokens equal to the number of shares they bought.
When a user sells shares back to the fund, the fund contract burns from their wallet a quantity of share tokens equal to the number of shares they sold. Since any purchase/sale of shares
causes `NetAssetValue` and `SharesOutstanding` to increase by equivalent values (in terms of KEKBGS), purchases/sales of shares do not directly affect the current share price. In practice,
the share price may be slightly affected due to slippage in the purchase/sale of assets when shares are bought/sold, but this price impact will not be significant.

The share token contract is deployed and owned by the mutual fund contract. Devs have no direct control over how share tokens are minted/burned; all of this behavior is specified in
the mutual fund contract code.

Issuing mutual fund shares as ERC20 tokens enables these share tokens to be freely transferred and exchanged between accounts. The share tokens could even be listed on decentralized exchanges.
The mutual fund contract is not concerned with the original purchaser of share tokens; any bearer of the fund's share tokens is able to sell them back to the fund at the current share price. This offers
much greater flexibility than a traditional mutual fund where investors typically do not have direct custody over their shares in the fund.

There is no limit to the number of shares that users can buy/sell from/to the mutual fund contract. Users are able to transact shares with the fund contract at the current share
price at any time. This share structure is similar to that of a traditional open-ended mutual fund.

### Minimum Deposit

### Disabling Deposits
Deposits are able to be disabled by the owner of the contract by calling `setDepositsEnabled(false)`. In this case, no new shares will be able to be purchased from the fund. Investors
will still be able to sell their current shares back to the fund at the current share price.

The contract owner can re-enable deposits by calling `setDepositsEnabled(true)`. The will enable users to buy shares from the fund again.

### Fees
The fund contract charges a 100 basis point deposit fee in $KEKBGS before shares are purchased. The contract owner is able to lower this fee in the future,
but the fee can never be set higher than the 100 basis points it was set to when the contract was deployed.

Revenue from the contract's deposit fees will primarily be used to grow the Kek Baggies project by covering expenses,
paying for marketing services, etc.

### Slippage

## Reserve Token

## Contract Addresses
* $KEKBGS - `0xe7A704EAA3232756C8504FCF01Dcb535dc2df2A2`
* Kek Baggies Mutual Fund - `0x91183C921f3E56E3e793Dd8A5A3ee8250c3CC9D7`
* Kek Baggies Mutual Fund Share Token - `0xa34A1adDE2dDDfB1FB54024285daB566E755e188`

## Disclaimer
Crypto assets are inherently risky and volatile. While we are attempting to mitigate overall risk by maintaining a diversified portfolio, we offer no promise nor guarantee that investments in the Kek Baggies Memecoin Mutual Fund will return a profit. Do not invest more than you are willing to lose.

The concept of a decentralized mutual fund deployed entirely on-chain is novel. There are no established precedents for how such a mutual fund contract should operate. While we have carefully evaluated the risks of the concept and extensively tested the contract for bugs and security vulnerabilities, we offer no warranty in the event of contract bugs or security breaches.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
