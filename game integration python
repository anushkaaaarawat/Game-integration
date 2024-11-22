import pygame
import random
import sys

# --------------------- Ludo Game ---------------------
def ludo_game():
    """Ludo game with basic movement simulation."""
    print("\nWelcome to Ludo!")
    players = int(input("Enter the number of players (2-4): "))
    tokens = [0] * players  # Token positions for each player
    winner = False

    while not winner:
        for i in range(players):
            print(f"\nPlayer {i + 1}'s turn.")
            input("Press Enter to roll the dice...")
            dice = random.randint(1, 6)
            print(f"Player {i + 1} rolled: {dice}")
            if tokens[i] + dice <= 30:  # Finish line at 30
                tokens[i] += dice
                print(f"Player {i + 1}'s token is now at position {tokens[i]}")
            else:
                print("Roll exceeds finish line! Try next turn.")
            if tokens[i] == 30:
                print(f"Player {i + 1} wins!")
                winner = True
                break

# --------------------- Snake Game ---------------------
def snake_game():
    """Snake game using pygame."""
    pygame.init()
    width, height = 600, 400
    screen = pygame.display.set_mode((width, height))
    pygame.display.set_caption("Snake Game")

    # Colors
    black = (0, 0, 0)
    white = (255, 255, 255)
    red = (213, 50, 80)
    green = (0, 255, 0)

    # Snake properties
    snake_block = 10
    snake_speed = 15
    snake_list = []
    snake_length = 1

    # Clock and food
    clock = pygame.time.Clock()
    food_x = round(random.randrange(0, width - snake_block) / 10.0) * 10.0
    food_y = round(random.randrange(0, height - snake_block) / 10.0) * 10.0

    # Initial snake position
    x = width // 2
    y = height // 2
    x_change = 0
    y_change = 0

    def draw_snake(snake_list):
        for block in snake_list:
            pygame.draw.rect(screen, green, [block[0], block[1], snake_block, snake_block])

    running = True
    while running:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                running = False
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_LEFT:
                    x_change = -snake_block
                    y_change = 0
                elif event.key == pygame.K_RIGHT:
                    x_change = snake_block
                    y_change = 0
                elif event.key == pygame.K_UP:
                    x_change = 0
                    y_change = -snake_block
                elif event.key == pygame.K_DOWN:
                    x_change = 0
                    y_change = snake_block

        x += x_change
        y += y_change

        if x >= width or x < 0 or y >= height or y < 0:
            print("Game Over!")
            break

        screen.fill(black)
        pygame.draw.rect(screen, red, [food_x, food_y, snake_block, snake_block])

        snake_head = [x, y]
        snake_list.append(snake_head)
        if len(snake_list) > snake_length:
            del snake_list[0]

        for block in snake_list[:-1]:
            if block == snake_head:
                print("Game Over!")
                running = False

        draw_snake(snake_list)

        if x == food_x and y == food_y:
            food_x = round(random.randrange(0, width - snake_block) / 10.0) * 10.0
            food_y = round(random.randrange(0, height - snake_block) / 10.0) * 10.0
            snake_length += 1

        pygame.display.update()
        clock.tick(snake_speed)
    pygame.quit()

# --------------------- Hangman Game ---------------------
def hangman_game():
    """Hangman game with a visual hanging man."""
    words = ["python", "hangman", "ludo", "snake", "integration", "apple", "banana"]
    word = random.choice(words).upper()
    guessed_word = "_" * len(word)
    attempts = 6
    guessed_letters = []

    stages = [
        """
           -----
           |   |
           O   |
          /|\\  |
          / \\  |
               |
        """,
        """
           -----
           |   |
           O   |
          /|\\  |
          /    |
               |
        """,
        """
           -----
           |   |
           O   |
          /|\\  |
               |
               |
        """,
        """
           -----
           |   |
           O   |
          /|   |
               |
               |
        """,
        """
           -----
           |   |
           O   |
           |   |
               |
               |
        """,
        """
           -----
           |   |
           O   |
               |
               |
               |
        """,
        """
           -----
           |   |
               |
               |
               |
               |
        """
    ]

    print("\nWelcome to Hangman!")
    while attempts > 0 and "_" in guessed_word:
        print(stages[attempts])
        print("\nWord:", " ".join(guessed_word))
        print("Attempts left:", attempts)
        print("Guessed letters:", ", ".join(guessed_letters))

        guess = input("\nGuess a letter: ").upper()
        if guess in guessed_letters:
            print("You already guessed that letter!")
            continue

        guessed_letters.append(guess)
        if guess in word:
            guessed_word = "".join([guess if letter == guess else guessed_word[i] for i, letter in enumerate(word)])
            print("Correct!")
        else:
            attempts -= 1
            print("Wrong guess!")

    if "_" not in guessed_word:
        print("\nCongratulations! You guessed the word:", word)
    else:
        print(stages[0])
        print("\nYou lost! The word was:", word)

# --------------------- Main Menu ---------------------
def main_menu():
    """Main menu for game selection."""
    while True:
        print("\n=== GAME INTEGRATION ===")
        print("1. Ludo Game")
        print("2. Snake Game")
        print("3. Hangman Game")
        print("4. Exit")
        choice = input("Choose a game (1-4): ")

        if choice == "1":
            ludo_game()
        elif choice == "2":
            snake_game()
        elif choice == "3":
            hangman_game()
        elif choice == "4":
            print("Exiting the game integration. Goodbye!")
            break
        else:
            print("Invalid choice! Please select a valid option.")

# --------------------- Start the Program ---------------------
if __name__ == "__main__":
    main_menu()
