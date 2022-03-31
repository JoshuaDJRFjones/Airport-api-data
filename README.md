# Airport-api-data
'''import json
import requests
from requests import get
import time


url = 'http://api.aviationstack.com/v1/flights?access_key=6c7edeb2e0f7ac335c6c026f73fb47aa_iata=OAK' 
one_arrival = get(url).json() 
one_departure = get(url).json()
total_arrive = (len(one_arrival['data']))

for i in range (0,total_arrive):
  print ("DEPARTURE")
  print (one_departure['data'][i]['departure']['airport'])
  landing_time=str(one_departure['data'][i]['departure']['estimated'])
  shorted_time=landing_time.replace(":00+00:00","")
  print(shorted_time) 
  print (one_departure['data'][i]['airline']['name'])
  print (one_departure['data'][i]['flight']['iata'])  
  print (" ")
  print ("ARRIVAL")
  landing_time=str(one_arrival['data'][i]['arrival']['estimated'])
  shorted_time=landing_time.replace(":00+00:00","")
  print (one_arrival['data'][i]['arrival']['airport'])
  print ("estimated arrival")
  print (shorted_time)
  print (one_arrival['data'][i]['airline']['name'])
  print (one_arrival['data'][i]['flight']['iata'])
  print ("flight status")
  print (one_arrival['data'][i]['flight_status'])
  print ("terminal")
  print (one_arrival['data'][i]['arrival']['terminal'])
  print ("gate")
  print (one_arrival['data'][i]['arrival']['gate'])
  print ("baggage claim")
  print (one_arrival['data'][i]['arrival']['baggage'])
  print ("---------------")
  # import pygame module in this program'''
import pygame
import time
from requests import get
import json
import io
import pygame as pg
#add your api key into this URL
url = "http://api.aviationstack.com/v1/flights?access_key=6c7edeb2e0f7ac335c6c026f73fb47aa&arr_iata=OAK"


 
# activate the pygame library
# initiate pygame and give permission
# to use pygame's functionality.
pygame.init()
 
# define the RGB value for white,
#  green, blue colour .
white = (255, 255, 255)
green = (0, 255, 0)
blue = (0, 0, 128)
black = (0, 0, 0)
orange = (0, 255, 0)
 
# assigning values to X and Y variable
X = 1280
Y = 900
 
# create the display surface object
# of specific dimension..e(X, Y).
display_surface = pygame.display.set_mode((X, Y))
#display_surface = pygame.display.set_mode((0, 0), pygame.FULLSCREEN)
 
# set the pygame window name
pygame.display.set_caption('Show Text')
 
# create a font object.
# 1st parameter is the font file
# which is present in pygame.
# 2nd parameter is size of the font
font = pygame.font.Font('freesansbold.ttf', 80)

 
# infinite loop
while True:
    one_departure = get(url).json()
    print (one_departure['data'][0]['departure']['airport'])
    #print(flight)
    print_flight=one_departure['data'][0]['departure']['airport']
    display_surface.fill(black)
    text = font.render(print_flight, True, black, orange)
    textRect = text.get_rect()
    textRect.center = (650,390)
    
    text2 = font.render("leaving oakland", True, white, black)
    textRect2 = text2.get_rect()
    textRect2.center = (650, 500)
    
    # copying the text surface object
    # to the display surface object
    # at the center coordinate.
    display_surface.blit(text, textRect)
    display_surface.blit(text2, textRect2)
    # Draws the surface object to the screen.
    pygame.display.update()
    time.sleep(20) #get new data every 20 seconds]
    

try:
    # Python2
    from urllib2 import urlopen
except ImportError:
    # Python3
    from urllib.request import urlopen
'''
# initialize pygame
pg.init()

# on a webpage right click on the image you want and use Copy image URL
image_url =""

image_str = urlopen(image_url).read()
# create a file object (stream)
image_file = io.BytesIO(image_str)

# (r, g, b) color tuple, values 0 to 255
white = (255, 255, 255)

# create a 1200x1000 white screen
screen = pg.display.set_mode((1200,1000),  pg.RESIZABLE )
screen.fill(white)

# load the image from a file or stream
image = pg.image.load(image_file)

# draw image, position the image ulc at x=20, y=20
screen.blit(image, (20, 20))

# nothing gets displayed until one updates the screen
pg.display.flip()

# start event loop and wait until
# the user clicks on the window corner x to exit
while True:
    for event in pg.event.get():
        if event.type == pg.QUIT:
            pg.quit()
            raise SystemExit


import io
import pygame as pg
try:
    # Python2
    from urllib2 import urlopen
except ImportError:
    # Python3
    from urllib.request import urlopen

# initialize pygame
pg.init()

# on a webpage right click on the image you want and use Copy image URL
image_url ="https://cutewallpaper.org/24/cartoon-plane-images/105751329.jpg"

image_str = urlopen(image_url).read()
# create a file object (stream)
image_file = io.BytesIO(image_str)

# (r, g, b) color tuple, values 0 to 255
white = (255, 255, 255)

# create a 1200x1000 white screen
screen = pg.display.set_mode((400,200),  pg.RESIZABLE )
screen.fill(white)

# load the image from a file or stream
image = pg.image.load(image_file)

# draw image, position the image ulc at x=20, y=20
screen.blit(image, (20, 20))

# nothing gets displayed until one updates the screen
pg.display.flip()

# start event loop and wait until
# the user clicks on the window corner x to exit
while True:
    for event in pg.event.get():
        if event.type == pg.QUIT:
            pg.quit()
            raise SystemExit
            '''
