# requirements
first of all you'll need to create a telegram bot and get a key. reach out @BotFather on telegram, the process is a walk-through so you should manage okay. put the key you get into a .env file in the working directory (the folder you're going to download/clone this code to). when the key is pasted into the file, write token=key exactly that way with no spaces and no apostrophes.

# intro
 **not financial advice**  
the purpose of this bot is to ensure constant return on a two-way arbitrage when sports betting; profit size is not dependant on which side wins.

# maths
this bot is only useful for american style odds and fraction odds. to be clear, american odds are shown as positive or negative three digit numbers (eg. 150, -110) and fractions odds are shown as fractions. positive american odds demonstrate profit from 100 bet, negative shows amount bet to make 100 profit. fractions odds show profit when multiplied by bet amount.

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

also, if the gain is less than 1 it means you'll lose money.

# further work
the third type to include is decimal odds, which is what exchanges like using. this feature will probably also need to include a commission factoring aspect. commission is exclusive to exchanges in my experience and most of my dealings have been with house controlled ones (easier to beat wrt. arb size).
