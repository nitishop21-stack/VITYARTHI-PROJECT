# VITYARTHI-PROJECT
"""
Rock : Paper (Paper)
Paper : Scissors (Scissors)
Rock : Scissors (Rock)
"""

import random
import sys

# --- ANSI Color Codes for Terminal Output ---
# These variables hold the strings that change the text color.
# We use BOLD for extra emphasis.
GREEN = '\033[1;32m' # Success/User Wins
RED = '\033[1;31m'   # Failure/Computer Wins
YELLOW = '\033[1;33m' # Tie/Neutral
CYAN = '\033[1;36m'  # Headers/Separators
ENDC = '\033[0m'     # Reset color to default
# ------------------------------------------

# --- Enhanced UI / Game Logic Variables ---
user_score = 0
computer_score = 0
tie_score = 0
round_num = 1
# ------------------------------------------

def inputHandler(inpt):
    inpt=inpt.lower()
    passOutput="rock paper scissors"
    r,p,s=passOutput.split()
    rval,pval,sval=0,0,0
    inptList=list(inpt)
    pList=[list(r),list(p),list(s)]
    for k in pList:
        i=0
        for l in k:
            try:
                if(l == inptList[i]):
                    if(k == list(r)):
                        rval+=1
                    elif(k == list(p)):
                        pval+=1
                    elif(k == list(s)):
                        sval+=1
                i+=1
            except IndexError:
                break
    if(rval == pval and pval == sval):
        print(f"\n\n{RED}❌ **Invalid input.** Please type 'rock', 'paper', or 'scissors'.{ENDC}")
        return None  # Return None for invalid input
    else:
        w=max(rval,pval,sval)
        if(w== rval):
            return r
        elif(w== pval):
            return p
        elif(w== sval):
            return s
        
            
    
# computer's choice
def computers_choice():
    # Returns -1 for Rock, 0 for Paper, 1 for Scissors
    return (random.choice([-1,0,1]))

def win_dec(user, computer):
    global user_score, computer_score, tie_score # Need to modify global scores
    
    if (user == computer):
        print(f"{YELLOW}🤝 **It's a TIE!**{ENDC}")
        tie_score += 1
    else:
        # Winning conditions: (User: Rock(-1) vs Comp: Scissors(1)) or (User: Paper(0) vs Comp: Rock(-1)) or (User: Scissors(1) vs Comp: Paper(0))
        if ((user == -1 and computer == 1) or (user == 0 and computer == -1) or  (user == 1 and computer == 0)):
            print(f"{GREEN}🎉 **USER WINS!**{ENDC}")
            user_score += 1
        else:
            print(f"{RED}🤖 **COMPUTER WINS!**{ENDC}")
            computer_score += 1

def display_scores():
    """Prints the current score board with colors."""
    print("\n" + CYAN + "="*40 + ENDC)
    print(f"{CYAN}         **CURRENT SCORE BOARD** {ENDC}")
    print("-" * 40)
    # Applying color dynamically to the scores based on win/loss/tie
    user_display = f"{GREEN}**{user_score}**{ENDC}" if user_score > computer_score else f"**{user_score}**"
    comp_display = f"{RED}**{computer_score}**{ENDC}" if computer_score > user_score else f"**{computer_score}**"
    tie_display = f"{YELLOW}**{tie_score}**{ENDC}"

    print(f"   User: {user_display} | Computer: {comp_display} | Ties: {tie_display}")
    print(CYAN + "="*40 + ENDC + "\n")


rps ={"rock":-1,"paper":0,"scissors":1}
revRPS={-1:"rock",0:"paper",1:"scissors"}
user = ""

print(f"{CYAN}✨ **Welcome to Rock, Paper, Scissors!** ✨{ENDC}")
display_scores()

while(True):
    print(f"--- {CYAN}**ROUND {round_num}**{ENDC} ---")

    uinput = input("Your choice (type 'rock', 'paper', 'scissors', or '0' to exit): ").strip()
    
    if (uinput == "0"):
        print(f"\n{CYAN}👋 **Thanks for playing! Final Score:**{ENDC}")
        display_scores()
        break
    
    user = inputHandler(uinput)
    
    if user is None:
        continue # Skip the rest of the loop for invalid input
        
    computer = computers_choice()
    
    print("\n" + "*"*20)
    print(f"You chose: **{user.upper()}**")
    print(f"Computer chose: **{revRPS[computer].upper()}**")
    print("*"*20)
    
    try:
        win_dec(rps[user],computer)
        display_scores()
        round_num += 1 # Increment round only on valid play
    except KeyError:
        print(f"{RED}\nAn unexpected error occurred. Exiting.{ENDC}")
        sys.exit() # Exit the program on unexpected error
