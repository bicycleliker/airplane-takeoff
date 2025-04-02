# airplane-takeoff
import time
import pygame

# Initialize Pygame
pygame.init()

# Screen settings
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Airplane Takeoff Simulator ✈️")

# Colors
WHITE = (255, 255, 255)
BLUE = (135, 206, 250)

# Load airplane image
airplane = pygame.image.load("airplane.png")  # Make sure to have an airplane image in the same directory
airplane = pygame.transform.scale(airplane, (100, 50))
plane_x, plane_y = WIDTH // 2 - 50, HEIGHT - 100

# Takeoff settings
speed = 2
takeoff = False
running = True
clock = pygame.time.Clock()

while running:
    screen.fill(BLUE)
    
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_SPACE:
                takeoff = True
    
    if takeoff:
        plane_y -= speed  # Move airplane up
        speed += 0.05  # Gradually increase speed for realism
    
    screen.blit(airplane, (plane_x, plane_y))
    pygame.display.flip()
    clock.tick(30)
    
pygame.quit()
6789
