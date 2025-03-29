# windmill-simulation
import pygame
import math

# Initialize pygame
pygame.init()

# Screen settings
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("🌬️ Windmill Simulation 🌿")

# Colors
WHITE = (255, 255, 255)
BLUE = (135, 206, 235)
BROWN = (139, 69, 19)
BLACK = (0, 0, 0)

# Windmill settings
CENTER_X = WIDTH // 2
CENTER_Y = HEIGHT // 2
BLADE_LENGTH = 100
angle = 0
speed = 2  # Speed of rotation

# Function to draw windmill
def draw_windmill():
    global angle
    
    # Draw tower
    pygame.draw.rect(screen, BROWN, (CENTER_X - 15, CENTER_Y, 30, 150))
    
    # Draw rotating blades
    for i in range(4):
        rad = math.radians(angle + i * 90)
        x = CENTER_X + BLADE_LENGTH * math.cos(rad)
        y = CENTER_Y + BLADE_LENGTH * math.sin(rad)
        pygame.draw.line(screen, BLACK, (CENTER_X, CENTER_Y), (x, y), 5)
    
    angle += speed  # Update rotation angle

# Game loop
running = True
clock = pygame.time.Clock()
while running:
    screen.fill(BLUE)
    
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
    
    draw_windmill()
    pygame.display.flip()
    clock.tick(30)

pygame.quit()
345
