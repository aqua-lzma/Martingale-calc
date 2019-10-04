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
<p align="center"><img src="/tex/69aff6635729e896201b951a07ac2380.svg?invert_in_darkmode&sanitize=true" align=middle width=135.85946715pt height=41.0933358pt/></p>

Summation:
<p align="center"><img src="/tex/0e531a317fbd085e7f07679d21e7c495.svg?invert_in_darkmode&sanitize=true" align=middle width=118.3041552pt height=36.1865163pt/></p>
