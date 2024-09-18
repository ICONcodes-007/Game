# Game
pip install pygame
import pygame
import sys

# Initialize Pygame
pygame.init()

# Set up display
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption('Simple Soccer Game')

# Colors
WHITE = (255, 255, 255)
GREEN = (34, 139, 34)
BLACK = (0, 0, 0)

# Ball settings
ball_radius = 15
ball_pos = [WIDTH // 2, HEIGHT // 2]
ball_speed = 5

# Main loop
clock = pygame.time.Clock()
running = True

while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Ball movement
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT]:
        ball_pos[0] -= ball_speed
    if keys[pygame.K_RIGHT]:
        ball_pos[0] += ball_speed
    if keys[pygame.K_UP]:
        ball_pos[1] -= ball_speed
    if keys[pygame.K_DOWN]:
        ball_pos[1] += ball_speed

    # Keep the ball within the screen bounds
    ball_pos[0] = max(ball_radius, min(WIDTH - ball_radius, ball_pos[0]))
    ball_pos[1] = max(ball_radius, min(HEIGHT - ball_radius, ball_pos[1]))

    # Drawing
    screen.fill(GREEN)  # Draw the field
    pygame.draw.circle(screen, WHITE, ball_pos, ball_radius)  # Draw the ball

    # Draw goals (rectangles on both ends)
    pygame.draw.rect(screen, WHITE, (WIDTH // 2 - 50, 0, 100, 30))  # Top goal
    pygame.draw.rect(screen, WHITE, (WIDTH // 2 - 50, HEIGHT - 30, 100, 30))  # Bottom goal

    # Update display
    pygame.display.flip()
    clock.tick(60)

pygame.quit()
sys.exit()
python soccer_game.py
