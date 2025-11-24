# VITYARTHI-PROJECT
import random
import sys

GREEN = '\033[1;32m'
RED = '\033[1;31m'
YELLOW = '\033[1;33m'
CYAN = '\033[1;36m'
ENDC = '\033[0m'

MOVES = ['rock', 'paper', 'scissors']

def get_standardized_choice(user_input):
    """
    Cleans up user input and matches it to a valid move.
    Allows for shortcuts like 'r' for rock.
    """
    clean_input = user_input.lower().strip()
    
    
    if clean_input in ['rock', 'r']:
        return 'rock'
    elif clean_input in ['paper', 'p']:
        return 'paper'
    elif clean_input in ['scissors', 's']:
        return 'scissors'
    
    return None

def get_computer_choice():
    """Randomly selects a move for the computer."""
    return random.choice(MOVES)

def determine_winner(user_move, computer_move):
    """
    Decides the winner.
    Returns: 'tie', 'user', or 'computer'
    """
    if user_move == computer_move:
        return 'tie'
    
    
    if (user_move == 'rock' and computer_move == 'scissors') or \
       (user_move == 'scissors' and computer_move == 'paper') or \
       (user_move == 'paper' and computer_move == 'rock'):
        return 'user'
    
    return 'computer'

def display_scoreboard(user_score, computer_score, ties):
    """Displays the current score with fancy formatting."""
    print(f"\n{CYAN}" + "="*40 + ENDC)
    print(f"{CYAN}         ** CURRENT SCORE BOARD ** {ENDC}")
    print("-" * 40)

    
    u_color = GREEN if user_score > computer_score else ENDC
    c_color = RED if computer_score > user_score else ENDC
    
    print(f"   User: {u_color}**{user_score}**{ENDC} | "
          f"Computer: {c_color}**{computer_score}**{ENDC} | "
          f"Ties: {YELLOW}**{ties}**{ENDC}")
    print(CYAN + "="*40 + ENDC + "\n")

def main():
    print(f"{CYAN} **Welcome to Rock, Paper, Scissors!** {ENDC}")
    
    user_score = 0
    computer_score = 0
    ties = 0
    round_num = 1

    while True:
        print(f"--- {CYAN}**ROUND {round_num}**{ENDC} ---")
        
        user_input = input("Your choice (rock/paper/scissors) or '0' to exit: ")
        
        if user_input == '0':
            print(f"\n{CYAN} **Thanks for playing! Final Result:**{ENDC}")
            display_scoreboard(user_score, computer_score, ties)
            break

        user_move = get_standardized_choice(user_input)

        if not user_move:
            print(f"{RED}Invalid input. Please type 'rock', 'paper', or 'scissors'.{ENDC}\n")
            continue

        computer_move = get_computer_choice()


        print("\n" + "*"*20)
        print(f"You chose:     **{user_move.upper()}**")
        print(f"Computer chose: **{computer_move.upper()}**")
        print("*"*20)

        # Decide winner
        result = determine_winner(user_move, computer_move)

        if result == 'tie':
            print(f"{YELLOW} **It's a TIE!**{ENDC}")
            ties += 1
        elif result == 'user':
            print(f"{GREEN} **YOU WIN this round!**{ENDC}")
            user_score += 1
        else:
            print(f"{RED}**COMPUTER WINS this round!**{ENDC}")
            computer_score += 1

        display_scoreboard(user_score, computer_score, ties)
        round_num += 1

if __name__ == "__main__":
    try:
        main()
    except KeyboardInterrupt:
        # Handles Ctrl+C gracefully
        print(f"\n{CYAN} Game exited.{ENDC}")
        sys.exit()
