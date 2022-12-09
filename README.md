# BlackJackPython
import random

def play():
    print("\n    WELCOME TO BLACKJACK ONLINE!\n")

    playerIn = True

    dealerIn = True

    deck = [2, 3, 4, 5, 6, 7, 8, 9, 10, 2, 3, 4, 5, 6, 7, 8, 9, 10, 2, 3, 4, 5, 6, 7, 8, 9, 10, 2, 3, 4, 5, 6, 7, 8, 9,
            10,
            'J', 'Q', 'K', 'A', 'J', 'Q', 'K', 'A', 'J', 'Q', 'K', 'A', 'J', 'Q', 'K', 'A']

    playerHand = []

    dealerHand = []

    def dealCard(turn):
        card = random.choice(deck)
        turn.append(card)
        deck.remove(card)

    def total(turn):
        total = 0
        ace = 0
        for card in turn:
            if card in range(1, 11):
                total += card
            elif card == "J" or card == "Q" or card == "K":
                total += 10
            else:
                total += 11
                ace += 1
        while ace and total > 21:
            total -= 10
            ace -= 1

        return total

    def XdealerHand():
        if len(dealerHand) >= 2:
            return dealerHand[0]

    for _ in range(2):
        dealCard(dealerHand)
        dealCard(playerHand)

    while playerIn or dealerIn:
        print(f'\n        Dealer has {XdealerHand()} and X')
        print(f'\n  You have {playerHand} for a total of {total(playerHand)}')
        if playerIn:
            stayOrHit = input('\n1: Stay\n\n2: Hit\n')
        if stayOrHit == '1':
            playerIn = False
        else:
            dealCard(playerHand)
            if total(playerHand) >= 21:
                break
            continue

        if total(dealerHand) > 16:
            dealerIn: False
            break
        else:
            dealCard(dealerHand)
        if total(playerHand) >= 21:
            break
        elif total(dealerHand) >= 21:
            break

    if total(playerHand) == 21:
        print(f'\n\n\n            You have {playerHand} for a total of {total(playerHand)}')
        print(f'\n            Dealer has {dealerHand} for a total of {total(dealerHand)}')
        print('\n                      Congratulations! You win!')
    elif total(dealerHand) == 21:
        print(f'\n\n\n            You have {playerHand} for a total of {total(playerHand)}')
        print(f'\n            Dealer has {dealerHand} for a total of {total(dealerHand)}')
        print('\n                       Dealer wins!')
    elif total(playerHand) > 21:
        print(f'\n\n\n            You have {playerHand} for a total of {total(playerHand)}')
        print(f'\n            Dealer has {dealerHand} for a total of {total(dealerHand)}')
        print('\n                   You went over 21! Dealer wins!')
    elif total(dealerHand) > 21:
        print(f'\n\n\n            You have {playerHand} for a total of {total(playerHand)}')
        print(f'\n            Dealer has {dealerHand} for a total of {total(dealerHand)}')
        print('\n                  Dealer went over 21! You win!')
    elif 21 - total(dealerHand) < 21 - total(playerHand):
        print(f'\n\n\n            You have {playerHand} for a total of {total(playerHand)}')
        print(f'\n            Dealer has {dealerHand} for a total of {total(dealerHand)}')
        print('\n                       Dealer wins!')
    elif 21 - total(playerHand) < 21 - total(dealerHand):
        print(f'\n\n\n            You have {playerHand} for a total of {total(playerHand)}')
        print(f'\n            Dealer has {dealerHand} for a total of {total(dealerHand)}')
        print('\n                       You win!')
    else:
        print(f'\n\n\n            You have {playerHand} for a total of {total(playerHand)}')
        print(f'\n            Dealer has {dealerHand} for a total of {total(dealerHand)}')
        print('\n                      Game is tied!')

while True:
    answer = input("\n      Would you like to play a game of Blackjack?\n 1:Yes\n 2:No\n").lower()
    if answer == '1':
        play()
    elif answer == '2':
        print('\n     COME BACK AND PLAY LATER! GOODBYE!')
        break
    else:
        print("Type 1 or 2")
