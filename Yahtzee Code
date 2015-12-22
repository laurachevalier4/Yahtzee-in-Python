dice = [0, 0, 0, 0, 0]
turn = 1
roll = 1
keep_going = "roll"
score_board = [["ones", 0], ["twos", 0], ["threes", 0], ["fours", 0], ["fives", 0], ["sixes", 0], ["3 of a kind", 0], ["4 of a kind", 0], ["full house", 0], ["small straight", 0], ["large straight", 0], ["yahtzee", 0], ["chance", 0]]
check_if_category = ["ones", "twos", "threes", "fours", "fives", "sixes", "3 of a kind", "4 of a kind", "full house", "small straight", "large straight", "yahtzee", "chance"]
used_score_categories = []
def score(list_of_dice, category):
    dice_counting = [0, 0, 0, 0, 0, 0]
    score = 0
    secondary_score = 0
    for element in score_board:
        if element[0] == category.lower():
            if category.lower() == "ones":
                for num in list_of_dice:
                    if num == 1:
                        score += 1
            elif category.lower() == "twos":
                for num in list_of_dice:
                    if num == 2:
                        score += 2
            elif category.lower() == "threes":
                for num in list_of_dice:
                    if num == 3:
                        score += 3
            elif category.lower() == "fours":
                for num in list_of_dice:
                    if num == 4:
                        score += 4
            elif category.lower() == "fives":
                for num in list_of_dice:
                    if num == 5:
                        score += 5
            elif category.lower() == "sixes":
                for num in list_of_dice:
                    if num == 6:
                        score += 6
            else:
                for num in list_of_dice:
                    if num == 1:
                        dice_counting[0] += 1
                    elif num == 2:
                        dice_counting[1] += 1
                    elif num == 3:
                        dice_counting[2] += 1
                    elif num == 4:
                        dice_counting[3] += 1
                    elif num == 5:
                        dice_counting[4] += 1
                    elif num == 6:
                        dice_counting[5] += 1
                if category.lower() == "3 of a kind":
                    for count in dice_counting:
                        if count == 3:
                            for die in list_of_dice:
                                score += die
                elif category.lower() == "4 of a kind":
                    for count in dice_counting:
                        if count == 4:
                            for die in list_of_dice:
                                score += die
                elif category.lower() == "full house":
                    for count in dice_counting:
                        if count == 3:
                            secondary_score += 3
                        elif count == 2:
                            secondary_score += 2
                    if secondary_score == 5:
                        score += 25
                elif category.lower() == "small straight":
                    for count in dice_counting:
                        if count == 0:
                            if dice_counting[5] == 0:
                                continue
                            else:
                                secondary_score = 0
                        elif count == 1 or count == 2:
                            secondary_score += 1
                        if secondary_score == 4:
                            score += 30
                elif category.lower() == "large straight":
                    for count in dice_counting:
                        if count == 0:
                            if dice_counting[5] == 0:
                                continue
                            else:
                                secondary_score = 0
                        if count == 1:
                            secondary_score += 1
                    if secondary_score == 5:
                        score += 40
                elif category.lower() == "yahtzee":
                    for num in list_of_dice:
                        if list_of_dice.index(num) == (list_of_dice[list_of_dice.index(num) - 1]):
                            score += num
                            continue
                        else:
                            break                       
                elif category.lower() == "chance":
                    for num in list_of_dice:
                        score += num               
            return score
        
        
        
def main():
    dice = [0, 0, 0, 0, 0]
    turns = range(13)
    score_board = [["ones", 0], ["twos", 0], ["threes", 0], ["fours", 0], ["fives", 0], ["sixes", 0], ["3 of a kind", 0], ["4 of a kind", 0], ["full house", 0], ["small straight", 0], ["large straight", 0], ["yahtzee", 0], ["chance", 0]]
    check_if_category = ["ones", "twos", "threes", "fours", "fives", "sixes", "3 of a kind", "4 of a kind", "full house", "small straight", "large straight", "yahtzee", "chance"]
    used_score_categories = []
    total_score = 0
    bonus = 0
    import random
    for turn in turns:
        roll = 0
        keep_going = "roll"
        while roll <= 2 and keep_going == "roll":
            count = 0
            print("Turn %s\n------" % (turn + 1))
            for die in dice:                    #Roll each die
                dice[count] = random.randint(1,6)
                count += 1
            print("You have rolled: %s." % dice)
            if roll == 2:
                roll += 1
                break
            roll += 1
            keep_going = input("Would you like to roll again? Insert 'roll' if yes, 'stop' if you would like to use these dice.\n> ")
            while keep_going.lower() != "stop" and keep_going.lower() != "roll":
                print("Invalid input.")
                keep_going = input("Would you like to roll again? Insert 'roll' if yes, 'stop' if you would like to use these dice.\n> ")
        if keep_going.lower() == "stop":
            score_category = input("What category would you like this to be scored under?\n> ")
        while score_category.lower() not in check_if_category:
            score_category = input("Invalid input. What category would you like this to be scored under?\n> ")
        while score_category.lower() in used_score_categories:
            score_category = input("You have already used this category. Please pick another.\n> ")
        used_score_categories.append(score_category.lower())
        scored = score(dice, score_category) 
        for element in score_board:
            if element[0] == score_category.lower():  #match player input with category in score board list 
                category_index = score_board.index(element)
        score_board[category_index][1] = scored
        print("Your current score board: %s\n" % score_board)
    for category in score_board:
        total_score += category[1]
    for category in range(6):
        bonus += score_board[category][1]
    if bonus >= 63:
        total_score += 35
    print("Upper total: %s" % bonus)
    if bonus >= 63:
        print("You have received a bonus of 35 points! Way to go, you!")
    print("Your total score is: %s" % total_score)
main()
