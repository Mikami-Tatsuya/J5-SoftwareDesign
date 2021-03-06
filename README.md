# J5-SoftwareDesign
2020 SoftwareDesgin 2

group development

## Team ｐｙてょｎ
### Members
 - Renta Noguchi (Leader)
 - Satoshi Naito
 - Reiji Yamashita
 - Tatsuya Mikami
 - Yu Miura

## Descriptions
development of Field Sugoroku with Python

The name is "日曜から夜ふかし \~Sunday midnight\~"

## Rule
 - 4\*5 Field
 - you can move Up,Down,Left,Right or stay only dice number
 - you should use events and satisfy win condition, you can win through.
 - player (2-4)
	 - initial position is corner of field.
 - win condition
	 - you have to satisfy any condition if you want to clear the game.
	 - when the game start, you get a condition.
 - event
	 - battle
		 - occurs when player get close
	 - shop
		 - placed on field
		 - you can get items by spend player status money
	 - job change
		 - placed on field
		 - you can change given job

## Extraction of materials
 - player
	 - status
		 - money
		 - muscle
		 - stress
		 - dexterity
	 - job
		 - teacher
		 - enginner
		 - sports man
		 - no job
	 - win condition
 - field
	 - event
		 - shop
		 - battle
		 - job change
 - dice

## Behiviour of materials
 - player
	 - moving Up,Down,Left,Right on field
	 - shopping and changing job in field
	 - battle other player
 - field
	 - placed on display, and provide field that player move
	 - player can battle, shop and change job here
 - dice
	 - put out 1~6 and effect player action

## Data structure
 - class "game"
```
class GAME():
	self.WIDTH		:variable of display width, passed from main function
	self.HEIGHT		:variable of display height, passed from main function
	self.MAG		:variable of display magnification, passed from main function
	self.root		:
	self.scene		:
	self.var_start_menu	:
	self.var_select_menu	:
	self.frame		:
	self.pressed		:
	canvas			:
	self.field		:instance of field inner status
	self.player		:instance array of player inner status
	self.turn		:flag that indicates active player
```
 - class "player"
```
class PLAYER():
	self.x			:variable of player x coordinate
	self.y			:variable of player y coordinate
	self.money		:variable of player money status
	self.muscle		:variable of player muscle status
	self.stress		:variable of player stress status
	self.dexterity		:variable of player dexterity staus
	self.job		:variable of player job
	self.condition		:variable of player win condition
```
 - class "field"
```
class FIELD():
	self.x			:variable of player x coordinate
	self.y			:variable of player y coordinate
	self.WIDTH		:variable of display width, passed from main function
	self.HEIGHT		:variable of display height, passed from main function
	self.num_shop		:variable of the number of shop
	self.num_jobchange	:variable of the number of jobchange
```

## Function specification
### Basic data structure
 - class "game"
```
class GAME():
	self.WIDTH		:variable of display width, passed from main function
	self.HEIGHT		:variable of display height, passed from main function
	self.MAG		:variable of display magnification, passed from main function
	self.root		:
	self.scene		:
	self.var_start_menu	:
	self.var_select_menu	:
	self.frame		:
	self.pressed		:
	canvas			:
	self.field		:instance of field inner status
	self.player		:instance array of player inner status
	self.turn		:flag that indicates active player
```
 - class "player"
```
class PLAYER():
	self.x			:variable of player x coordinate
	self.y			:variable of player y coordinate
	self.money		:variable of player money status
	self.muscle		:variable of player muscle status
	self.stress		:variable of player stress status
	self.dexterity		:variable of player dexterity staus
	self.job		:variable of player job
	self.condition		:variable of player win condition
```
 - class "field"
```
class FIELD():
	self.x			:variable of player x coordinate
	self.y			:variable of player y coordinate
	self.WIDTH		:variable of display width, passed from main function
	self.HEIGHT		:variable of display height, passed from main function
	self.num_shop		:variable of the number of shop
	self.num_jobchange	:variable of the number of jobchange
```

### Basic function specification
 - class "game"
```
class GAME():
	def __init__():
		argument:self, width, height, root
		return value:none
		# initialize some constant and variables in GAME class
		# initialize keyboard config
		# call start_menu() function
	def key_pressed()
		argument:event
		return value:none
		# when key pressed, call this function
		# add pressed key from array
	def key_released()
		argument:event
		return value:none
		# when key released, call this function
		# delete released key from array
	def start_menu()
		argument:none
		return value:0
		# display start menu
		# create menu screen by canvas and label
		# control Up, Down and Enter key
		# you can be Game Start or Exit here
	def select_menu()
		argument:none
		return value:0
		# display select manu
		# create menu screen by some label
		# control Up, Down, Left, Right and Enter key
		# you can be select the number of player and start game
		# decide each player's initial position by the number of player
	def start()
		argument:none
		return value:none
		# function calling function that processing
		# call print_field()
		# call move_player()
		# call check_win_condition()
		# call check_exit_condition()
	def print_field()
		argument:none
		return value:none
		# print field using field instance
		# print player status using player instance
		# change the number of status display and position by the number of player
	def roll_dice()
		argument:none
		return value:none
		# function that decide dice number using random number
	def check_win_condition()
		argument:none
		return value:none
		# function that checking satisfy condition
		# if player satisfy conidition, put true to condition of class player
	def check_exit_condition()
		argument:none
		return value:none
		# checking function exit condition of game
		# call show_result() if all player win condition satisfy
	def move_player()
		argument:none
		return value:none
		# function that move placed player on field
		# player can move range of field
	def show_result()
		argument:none
		return value:none
		# show grade of player
```
 - class "player"
```
class PLAYER():
	def __init__():
		argument:none
		return value:none
		# initialize player's status
		# money, muscle, stress, job, DEX
		# give player win condition
		# call decide_job and give player job
	def decide_job():
		argument:none
		return value:none
		# decide job by random
		# there are 4 jobs 'Teacher', 'Engineer', 'SportsMan' and 'Nojob'
```
 - class "field"
```
class FIELD():
	def __init__():
		argument:none
		return value:none
		# initialize field properties
		# x, y, number of shop, number of job change point and field array
	def set_field():
		argument:none
		return value:x, y
		# setting　field size x, y
	def set_events()
		argument:none
		return value:number of shop, number of job change point
		# setting number of event point shop and job change
	def init_field():
		argument:x, y, number of shop, number of job change point
		return value:field array
		# initialize internal information of field
		# random create point of shop and jobchange
		# other points initialized by 'Normal'
```
