#Flow Free Solution. Color Connection. Phillip Hale 11/16/2014
from tkinter import *

path1=[] #starting point
path2=[] #ending point

def callback(r,c):
    global player


    if player == 'R' and states[r][c] == 0 and stop_game==False:
        b[r][c].configure(text='0', fg='red', bg='white')
        states[r][c] = 'R'
        default[r][c] = 'R'
        path1.append((r,c))
        player = 'R*'

    if player == 'R*' and states[r][c] == 0 and stop_game==False:
        b[r][c].configure(text='0', fg='red', bg='black')
        states[r][c] = 'R*'
        default[r][c] = 'R*'
        path2.append((r,c))
        player = 'B'

    if player == 'B' and states[r][c] == 0 and stop_game==False:
        b[r][c].configure(text='1', fg='blue', bg='white')
        states[r][c] = 'B'
        default[r][c] = 'B'
        path1.append((r,c))
        player = 'B*'

    if player == 'B*' and states[r][c] == 0 and stop_game==False:
        b[r][c].configure(text='1', fg='blue', bg='black')
        states[r][c] = 'B*'
        default[r][c] = 'B*'
        path2.append((r,c))
        player = 'G'

    if player == 'G' and states[r][c] == 0 and stop_game==False:
        b[r][c].configure(text='2', fg='green', bg='white')
        states[r][c] = 'G'
        default[r][c] = 'G'
        path1.append((r,c))
        player = 'G*'

    if player == 'G*' and states[r][c] == 0 and stop_game==False:
        b[r][c].configure(text='2', fg='green', bg='black')
        states[r][c] = 'G*'
        default[r][c] = 'G*'
        path2.append((r,c))
        player = 'P'

    if player == 'P' and states[r][c] == 0 and stop_game==False:
        b[r][c].configure(text='3', fg='purple', bg='white')
        states[r][c] = 'P'
        default[r][c] = 'P'
        path1.append((r,c))
        player = 'P*'

    if player == 'P*' and states[r][c] == 0 and stop_game==False:
        b[r][c].configure(text='3', fg='purple', bg='black')
        states[r][c] = 'P*'
        default[r][c] = 'P*'
        path2.append((r,c))
        player = 'Y'

    if player == 'Y' and states[r][c] == 0 and stop_game==False:
        b[r][c].configure(text='4', fg='gold', bg='white')
        states[r][c] = 'Y'
        default[r][c] = 'Y'
        path1.append((r,c))
        player = 'Y*'

    if player == 'Y*' and states[r][c] == 0 and stop_game==False:
        b[r][c].configure(text='4', fg='gold', bg='black')
        states[r][c] = 'Y*'
        default[r][c] = 'Y*'
        path2.append((r,c))
        startQueue()

def startQueue():
    global stop_game, queue, found, queue2, pathway, maze

    pathway = []
    while len(path1) > 0:
        x,y = path1.pop(0)
        queue = [(x,y)]
        print(maze[x][y],"Starting Path #:", queue)
        maze[x][y] = 1
        x,y = path2.pop(0)
        queue2 = [(x,y)]
        print(maze[x][y],"Ending Path #:", queue2)
        maze[x][y] = 'x'
        le(queue)
        print('\n'.join([''.join(['{:2}'.format(item) for item in row])
            for row in maze]))
        leSteps(queue2,x,y)
        found = True
        clear = [row[:] for row in default]
        maze = clear

    for i, v in enumerate(pathway): #When looping through a sequence, the position index and corresponding value
        print(i,v)                  # can be retrieved at the same time using the enumerate() function.

    for k,w in enumerate(pathway):
        for x,y in w:
            maze[x][y]=k
            b[x][y].configure(text=k, bg='gray')


    print('\n'.join([''.join(['{:2}'.format(item) for item in row])
        for row in maze]))



    stop_game = True

def valid(x,y):		# Check coordinate within maze rectangle
  return (
    0 <= x < W and
    0 <= y < H)

def moves(x,y): return (# Returns octuple of coordinates one move from (x,y).
  (x+0,y+1), (x+0,y-1),	#   NOTE:  Some may be outside rectangular maze.
  (x+1,y+0), (x-1,y+0))

def move(x,y):		# Add neighbors of X,Y to queue and mark with cost.
  global queue, found		# Queue is global fifo of points
  c = maze[x][y]+1	# It costs one step to move from here to there

  for x,y in moves(x,y):	# Loop through neighbors of (X,Y):
    if valid(x,y) and maze[x][y] == 'x':
        maze[x][y] = c
        print(x,y)
        found = False
    elif valid(x,y) and maze[x][y] == 0:		#   haven't already been there,
        queue.append((x,y))	#     put neighbor onto end of queue
        maze[x][y] = c		#     change cost from '.' to number of steps.


def retrace(x,y):	# Return a neighbor of X,Y one step closer to start
  c = maze[x][y]-1	# Cost of neighbor that's one step closer
  for x,y in moves(x,y):# Loop through neighbors of (X,Y)
    if (valid(x,y) and 	#   If inside maze and
    maze[x][y] == c): 	#   exactly one step closer to start,
      return x,y	#     return another step backward




def le(queue):
    while queue and found:
        x,y = queue.pop(0)
        move(x,y)

def leSteps(queue2,x,y):    #show the steps
    global pathway
    print(x,y)
    steps = [(x,y)]
    pathway.append(steps)
    print(steps, maze[x][y])
    while maze[x][y] > 1:			# Until back at (0,0):
        x,y = retrace(x,y)		#   Take a step back
        steps.append((x,y))	#   Add new location to list

    steps.reverse()
    print (len(steps), "points: ", steps)

root = Tk()

b = [[0,0,0,0,0],
     [0,0,0,0,0],
     [0,0,0,0,0],
     [0,0,0,0,0],
     [0,0,0,0,0]]

states = [[0,0,0,0,0],
          [0,0,0,0,0],
          [0,0,0,0,0],
          [0,0,0,0,0],
          [0,0,0,0,0]]

default = [[0,0,0,0,0],
          [0,0,0,0,0],
          [0,0,0,0,0],
          [0,0,0,0,0],
          [0,0,0,0,0]]

maze = states

W = len(maze[0])	# Width of maze (characters in first row)
H = len(maze)		# Height of maze (number of rows)
found = True

for i in range(5):
    for j in range(5):
        b[i][j] = Button(font=('Verdana', 56), width=3, bg='yellow',
                         command = lambda r=i,c=j: callback(r,c))
        b[i][j].grid(row = i, column = j)

player = 'R'
stop_game = False







mainloop()
