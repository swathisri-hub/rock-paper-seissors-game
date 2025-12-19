import random

print("Welcome to AI + ML Rock Paper Scissors Game")
print("Type: rock, paper, or scissors")
print("Type 'exit' to quit\n")

choices = ["rock", "paper", "scissors"]
user_history = []   # ML learning data
score_user = 0
score_ai = 0

def ai_choice_ml(user_history):
    # If no previous data, choose randomly
    if not user_history:
        return random.choice(choices)

    # ML: find user's most frequent choice
    most_common = max(set(user_history), key=user_history.count)

    # AI logic: counter user's habit
    if most_common == "rock":
        return "paper"
    elif most_common == "paper":
        return "scissors"
    else:
        return "rock"

while True:
    user = input("Your choice: ").lower()

    if user == "exit":
        print("\nGame Over!")
        print(f"Final Score -> You: {score_user} | AI: {score_ai}")
        break

    if user not in choices:
        print("Invalid choice! Try again.\n")
        continue

    user_history.append(user)
    ai = ai_choice_ml(user_history)

    print("AI chose:", ai)

    if user == ai:
        print("It's a tie!\n")
    elif (user == "rock" and ai == "scissors") or \
         (user == "paper" and ai == "rock") or \
         (user == "scissors" and ai == "paper"):
        print("You win this round!\n")
        score_user += 1
    else:
        print("AI wins this round!\n")
        score_ai += 1

    print(f"Score -> You: {score_user} | AI: {score_ai}\n")

