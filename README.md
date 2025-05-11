# intro
the purpose of this bot is to ensure constant return on a two-way arbitrage when sports betting; profit size is not dependant on which side wins.
this isn't financial advice by the way, i would hope though by the nature of what is being done here that nobody would consider it that.

```
import telegram_bot_api as tb_api
import telebot
import time
```

`telegram_bot_api` is another .py file that contains: `token = 'api_key'` in that exact format.
the python code used + logic is simple enough so anything confusing is probably specific to telegram and explained in thier docs.

# maths
this bot is only useful for american style odds and fraction odds. to be clear, american odds are shown as positive or negative three digit numbers (eg. 150, -110) and fractions odds are shown as... fractions. positive american odds demonstrate profit from 100 bet, negative shows amount bet to make 100 profit. fractions odds show profit when multiplied by bet amount.

the maths itself in the code may seem confusing, that's because it's a final derivation not the original, full workings is as follows:

```
cost = (bet size 1) + (bet size 2)
return 1 = (bet size 1)(odds 1) + (bet size 1)
return 2 = (bet size 2)(odds 2) + (bet size 2)
return 1 - cost = return 2 - cost
(bet size 1)(odds 1) - (bet size 2) = (bet size 2)(odds 2) - (bet size 1)
(bet size 1)(odds 1) + (bet size 1) = (bet size 2)(odds 2) + (bet size 2)
(bet size 1) = ((bet size 2)((odds 2) + 1))/((odds 1) + 1)
```

# using it
you need to type odds and if odds are american, type american. if not american type anything at all. this probably sounds confusing so here's a picture:

![IMG_2905](https://github.com/user-attachments/assets/8a41b786-7d19-408a-b1db-5ab97cb79ab4)

don't worry about spaces because the code line `words = [word.strip() for word in message.text.split(',')]` strips the entry message to words based on comma placement.
the gain states equity growth in decimal form inclusive of current equity. in simpler terms, multiply it by all the money your going to use on this trade to see how much you'll be left with after (dependant on if the bookies play fair).

also, if the gain is less than 1 it means you'll lose money, just in an optimal way (lol).

# further work
the third type to include is decimal odds, which is what exchanges like using. this feature will probably also need to include a commission factoring aspect. commission is exclusive to exchanges in my experience and most of my dealings have been with house controlled ones (easier to beat wrt. arb size).
