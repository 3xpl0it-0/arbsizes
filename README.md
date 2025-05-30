# requirements
first of all you'll need to create a telegram bot and get a key. reach out to @BotFather on telegram, the process is a walk-through so you should manage okay. put the key you get into a .env file in the working directory (the folder you're going to download/clone this code to). when the key is pasted into the file, write token=key exactly that way with no spaces and no apostrophes.

next steps, you'll need the following libraries installed: python-dotenv, telebot. the others are already installed with python.

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
firstly, when you run the code you'll need to send /start or /help to the bot to start it.

for bets, you need to type odds and if odds are american, type american. if not american type anything at all. if you're typing in fractions you need to use / instead of \ or it won't work. this all probably sounds confusing so here's a picture:

![image not loading](https://github.com/3xpl0it-0/arbsizes/blob/main/IMG_2905.jpg)

don't worry about spaces because the code line `words = [word.strip() for word in message.text.split(',')]` strips the entry message to words based on comma placement.
the gain states equity growth in decimal form inclusive of current equity. in simpler terms, multiply it by all the money your going to use on this trade to see how much you'll be left with after (dependant on if the bookies play fair). if you type something in incorrectly and don't get a response wait a few seconds and try againn.

also, if the gain is less than 1 it means you'll lose money.

# further work
the third type to include is decimal odds, which is what exchanges like using. this feature will probably also need to include a commission factoring aspect. commission is exclusive to exchanges in my experience and most of my dealings have been with house controlled ones (easier to beat wrt. arb size).
