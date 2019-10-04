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
$$
bankroll - bet + (bet\times payout)
$$

If we treat bankroll as `1` and the bet as the initial bet fraction the profit is:
$$
1 - bet + (bet\times payout)
$$

The amount you should bet on the first phase is dependant on how many betting phases you've decided carries an acceptable risk of bankruptcy. Obviously, the lower the chance the lower the profit per round. The faction of your bankroll that you should bet on the first phase should be 1 over the sum of betting phases times your payout. In code:
```
sum = 0
for n = 1 to phases
  sum = sum + (n * payout)
bet = 1 / sum
```
Math notation:
$$
bet = \frac{1}{\sum_{n=1}^{phases}payout^{n-1}}
$$

Summation:
$$
bet = \frac{payout-1}{payout^{phases}-1}
$$

So now we can calculate the profit as this:
$$
profit = 1 - \frac{payout - 1}{payout^{phases}-1} + (\frac{payout - 1}{payout^{phases}-1} * payout)
$$

Simplified:
$$
profit = \frac{(payout - 1)^2}{payout^{phases}-1}+1
$$

If you graph this you might notice that the profit is actually higher on lower payouts. This is because you're betting a higher fraction of your bank on higher payouts. But in real life the risk will be higher on larger payouts, so next we work out the actual profit per risk on a specific bet / payout.

The risk of going bankrupt is simply the chance of failure multiplied by itself for each betting phase. Or the fail chance to the power of betting phases.
$$
risk = (\frac{fail chance}{total chance})^{phases}
$$

This makes the risk a bit arbitrary because its defined by how many phases you should do so instead we'll work out how many phases you should do to meet a desired risk thershold.
$$
phases = -\frac{\log({risk})}{\log({\frac{total chance}{fail chance}})}
$$
