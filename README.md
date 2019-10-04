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

Your profit per round following this system is <p align="center"><img src="/tex/2a27241f01be052c656b00fff9aedcf0.svg?invert_in_darkmode&sanitize=true" align=middle width=224.25630315pt height=16.438356pt/></p>. If we treat bankroll as `1` and the bet as the initial bet fraction the profit is <p align="center"><img src="/tex/579dda2f2a66a74b82a8c663fd3025c7.svg?invert_in_darkmode&sanitize=true" align=middle width=171.491628pt height=16.438356pt/></p>.

The amount you should bet on the first phase is dependant on how many betting phases you've decided carries an acceptable risk of bankruptcy. Obviously, the lower the chance the lower the profit per round. The faction of your bankroll that you should bet on the first phase should be 1 over the sum of betting phases times your payout. $$\frac{1}{\sum_{n=1}^{phases}payout^{n-1}}.
