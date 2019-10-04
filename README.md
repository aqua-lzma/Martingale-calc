# Martingale-calc
Martingale betting system calculator

*[Click here to learn the basics of the Marginale system](https://en.wikipedia.org/wiki/Martingale_(betting_system))*

This calculator is for a slightly modified version thats more applicable to more types of games. Instead of the Martingale system where you *double* your bet every time you lose, you simply multiply it by the payout of the bet. Assuming you win every round eventually, the profit you make per round should remain constant. This calculator allows you to work which chance / payout combination is most ideal for profit per round in consideration of your accepted risk of bankruptcy.

**Example** for a bet a **3 times payout**. Playing modified Martingale with 3 betting phases.
(Using a starting bank value of 13 for ease of division.):

| Phase | Bank | Bet | Bank if won             | Bank if lost |
| ----- | ---- | --- | ----------------------- | ------------ |
| 1     | 13   | 1   | (13 - 1) + (1 * 3) = 15 | 12           |
| 2     | 12   | 3   | (12 - 3) + (3 * 3) = 15 | 9            |
| 3     | 9    | 9   | (9 - 9) + (9 * 3) = 15  | 0            |

Your profit per round following this system is:
<p align="center"><img src="/tex/2574dde0718a23d264d933eec5f88bab.svg?invert_in_darkmode&sanitize=true" align=middle width=224.25630315pt height=16.438356pt/></p>

If we treat bankroll as `1` and the bet as the initial bet fraction the profit is:
<p align="center"><img src="/tex/497e175cfad2fa0d86ff9e52334c4bca.svg?invert_in_darkmode&sanitize=true" align=middle width=171.491628pt height=16.438356pt/></p>

The amount you should bet on the first phase is dependant on how many betting phases you've decided carries an acceptable risk of bankruptcy. Obviously, the lower the chance the lower the profit per round. The faction of your bankroll that you should bet on the first phase should be 1 over the sum of betting phases times your payout. In code:
```
sum = 0
for n = 1 to phases
  sum = sum + (n * payout)
fraction = 1 / sum
```
Math notation:
<p align="center"><img src="/tex/2ac85d760bc2a190727adf30c493c15a.svg?invert_in_darkmode&sanitize=true" align=middle width=222.67727295pt height=41.0933358pt/></p>

Summation:
<p align="center"><img src="/tex/ed325a2c8d30d76054cfb0dc61e452f5.svg?invert_in_darkmode&sanitize=true" align=middle width=205.12196099999997pt height=36.1865163pt/></p>

If you graph this you might notice that the profit is actually higher on lower payouts. This is because you're betting a higher fraction of your bank on higher payouts. But in real life the risk will be higher on larger payouts, so next we work out the actual profit per risk on a specific bet / payout.

The risk of going bankrupt is simply the chance of failure multiplied by itself for each betting phase. Or the fail chance to the power of betting phases.
<p align="center"><img src="/tex/5436ecc0ba416fd3fa0eefc4402bb3ff.svg?invert_in_darkmode&sanitize=true" align=middle width=201.45553065pt height=33.81208709999999pt/></p>

This makes the risk a bit arbitrary because its defined by how many phases you should do so instead we'll work out how many phases you should do to meet a desired risk thershold.
<p align="center"><img src="/tex/8a27c350aa049f771eb59819fdf9423a.svg?invert_in_darkmode&sanitize=true" align=middle width=182.80224435pt height=43.0970364pt/></p>

