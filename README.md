# Soft-fur-
Licht 
import pygame
import sys
import random

# Initialize Pygame
pygame.init()

# Set up display
width, height = 800, 600
screen = pygame.display.set_mode((width, height))
pygame.display.set_caption('Light Effects')

# Colors
BLACK = (0, 0, 0)
WHITE = (255, 255, 255)
YELLOW = (255, 255, 0)

# Light position and radius
light_pos = [width // 2, height // 2]
light_radius = 50

# Main game loop
while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    # Clear the screen
    screen.fill(BLACK)

    # Draw light source
    pygame.draw.circle(screen, YELLOW, light_pos, light_radius)

    # Draw rays of light
    for _ in range(10):
        angle = random.uniform(0, 2 * 3.1416)
        length = random.uniform(10, 100)
        end_pos = [light_pos[0] + length * pygame.math.Vector2(1, 0).rotate(angle).x,
                   light_pos[1] + length * pygame.math.Vector2(1, 0).rotate(angle).y]

        pygame.draw.line(screen, WHITE, light_pos, end_pos, 2)

    pygame.display.flip()
