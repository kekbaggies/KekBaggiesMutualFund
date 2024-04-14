# Kek Baggies Memecoin Mutual Fund

The Kek Baggies Memecoin Mutual Fund is a smart contract operating as a pooled investment fund for a basket of memecoins and other tokens on the Base chain.
Our goal is to seek returns by providing exposure to the memecoin market while reducing overall risk through diversification.
The fund provides to investors a convenient way to invest in memecoins without having to put in the effort of manually managing their own crypto portfolio.

The mutual fund is deployed entirely on-chain, enabling us to operate with much greater transparency and decentralization than investors would be
able to experience with a traditional mutual fund.

This README is intended to serve as a complete documentation of the mutual fund contract and the web interface for interacting with it.

If you have any questions or concerns, please join us on [Telegram](https://t.me/KekBaggiesToken).

## Contents
* [Quickstart](#quickstart)
    * [Buying Shares](#buying-shares)
    * [Selling Shares](#selling-shares)
* [Mutual Fund Structure](#mutual-fund-structure)
    * [Contract](#contract)
    * [Portfolio Management](#portfolio-management)
    * [Shares](#shares)
    * [Fees](#fees)
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

### Portfolio Management

### Shares

### Fees
The fund contract charges a 100 basis point deposit fee in $KEKBGS before shares are purchased. This fee is able to be lowered in the future,
but can never be set higher than the 100 basis points it was set to when the contract was deployed.

Revenue from the contract's deposit fees will primarily be used to grow the Kek Baggies project by covering expenses,
paying for marketing services, etc.

## Reserve Token

## Contract Addresses
* $KEKBGS - `0xe7A704EAA3232756C8504FCF01Dcb535dc2df2A2`
* Kek Baggies Mutual Fund - `0x91183C921f3E56E3e793Dd8A5A3ee8250c3CC9D7`
* Kek Baggies Mutual Fund Share Token - `0xa34A1adDE2dDDfB1FB54024285daB566E755e188`

## Disclaimer
Crypto assets are inherently risky and volatile. While we are attempting to mitigate overall risk by maintaining a diversified portfolio, we offer no promise nor guarantee that investments in the Kek Baggies Memecoin Mutual Fund will return a profit. Do not invest more than you are willing to lose.

The concept of a decentralized mutual fund deployed entirely on-chain is novel. There are no established precedents for how such a mutual fund contract should operate. While we have carefully evaluated the risks of the concept and extensively tested the contract for bugs and security vulnerabilities, we offer no warranty in the event of contract bugs or security breaches.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
