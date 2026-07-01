---
layout: single
title: "[Tkinter] Tic Tac Toe"
classes: wide
categories:
  - python project
---

# Tic Tac Toe GUI  

![image](https://user-images.githubusercontent.com/47412229/209776495-e44d18ce-675a-468f-8bd4-276b595ae05b.png)


```python

from tkinter import *
from tkinter import messagebox
import random

################################################################################################################
class Board():
    board=[[],[],[]]
    position = {1:"0,0", 2:"0,1", 3:"0,2",
                4:"1,0", 5:"1,1", 6:"1,2", 
                7:"2,0", 8:"2,1", 9:"2,2"}
    board_check_list = [1,2,3,4,5,6,7,8,9]
    lbl = None
    player_change = 1    
    def __init__(self):
        for row in range(3):
            for col in range(3):
                self.board[row].append(self.button(root))
                self.board[row][col].config(command=lambda row=row, col=col:self.play(row, col))
                self.board[row][col].grid(row=row, column=col)
            
        self.lbl = self.state_label(root)
        btn = Button(root, text="CLEAR", font=("arial", 14, "bold"), command=self.board_clear)
        btn.grid(row=3, column=2)
        
    def state_label(self, frame):
        lbl = Label(frame, text="Play Game", font=("arial", 20, "bold"))
        lbl.grid(row=3, column=0, columnspan=2)
        return lbl   
    
    def board_clear(self):
        for row in range(3):
            for col in range(3):
                Board.board[row][col].config(state = NORMAL, 
                                            text = "",
                                            bg="papaya whip")
        self.lbl["text"] = "Play Game"
        self.board_check_list = [1,2,3,4,5,6,7,8,9]                                      
     
    def button(self, frame):
        btn=Button(frame, text="", 
               padx=1, bg="papaya whip", 
               width=3, font=('arial',30,"bold"),
               relief="sunken", bd=5)
        return btn
    
    def play(self, row, col):
        pos = -1        
        for k, v in self.position.items():
            if v == str(row)+","+str(col) :
                pos = k
        print(pos)
        if self.player_change == 1:
            x_player.select_block(row, col)
            self.board_check_list.remove(pos)
            print(self.board_check_list)
            
            if Check.win() :
                print("X win")
                self.lbl["text"] = "X win"
                Check.game_over()
            elif Check.draw() :
                print("Draw")
                self.lbl["text"] = "Draw"
            else: # ai Play
                Ai.ai_play(self.board_check_list, self.lbl)
                                
        #else :            
            # 2 player
            #o_player.select_block(row, col)
            #
            #if Check.win(o_player.player) :
            #    print("O win")
            #    self.lbl["text"] = "O win"
            #    Check.game_over()
            #elif Check.draw():
            #    print("Draw")
            #    self.lbl["text"] = "Draw"
            #else:
            #    self.player_change *= -1
class Ai() :
    def ai_play(board_check_list, lbl):
        if board_check_list != [] :
            pos = random.choice(board_check_list)
            print(pos)
            board_check_list.remove(pos)
            print(board_check_list)
            row, col = Board.position[pos].split(",")
            o_player.select_block(int(row), int(col))
                    
            if Check.win() :
                print("O win")
                lbl["text"] = "O win"
                Check.game_over()
            elif Check.draw() :
                print("Draw")
                lbl["text"] = "Draw"
               
################################################################################################################
class Player():
    player =""
    def __init__(self, player):
       self.player = player   
     
    def select_block(self, row, col):
        Board.board[row][col]["text"] = self.player
        
        # player color : X - deep sky blue / O - lawn green
        if self.player == "X":
                Board.board[row][col].config(state=DISABLED, disabledforeground="deep sky blue")
        elif self.player == "O":
            Board.board[row][col].config(state=DISABLED, disabledforeground="lawn green")
################################################################################################################
                    
################################################################################################################
class Check() :
    def win():
        if (Board.board[0][0]["text"] == Board.board[0][1]["text"] == Board.board[0][2]["text"] !=""):
            return True
        elif (Board.board[1][0]["text"] == Board.board[1][1]["text"] == Board.board[1][2]["text"] !=""):
            return True
        elif (Board.board[2][0]["text"] == Board.board[2][1]["text"] == Board.board[2][2]["text"] !=""):
            return True
        elif (Board.board[0][0]["text"] == Board.board[1][0]["text"] == Board.board[2][0]["text"] !=""):
            return True
        elif (Board.board[0][1]["text"] == Board.board[1][1]["text"] == Board.board[2][1]["text"] !=""):
            return True
        elif (Board.board[0][2]["text"] == Board.board[1][2]["text"] == Board.board[2][2]["text"] !=""):
            return True
        elif (Board.board[0][0]["text"] == Board.board[1][1]["text"] == Board.board[2][2]["text"] !=""):
            return True
        elif (Board.board[2][0]["text"] == Board.board[1][1]["text"] == Board.board[0][2]["text"] !=""):
            return True
        else:
            return False
        
    def draw():
        for row in range(3):
            for col in range(3):
                if Board.board[row][col]["text"] == "" :
                    return False
        return True
    
    def game_over():
        for row in range(3):
            for col in range(3):
                Board.board[row][col]["state"] = DISABLED 
################################################################################################################


# main - begin
root = Tk()
root.title("Tic Tac Toe")
root.resizable(False, False)

board = Board()
x_player = Player("X")
o_player = Player("O")

root.mainloop()
# main - end
```  

## minimax 알고리즘을 적용한 Tic Tac Toe

```python

from tkinter import *
from threading import Thread
import random
################################################################################################################
class Board():
    board=[[],[],[]]
    lbl = None       
    def __init__(self):
        for row in range(3):
            for col in range(3):
                self.board[row].append(self.button(root))
                self.board[row][col].config(command=lambda row=row, col=col:self.play(row, col))
                self.board[row][col].grid(row=row, column=col)
        self.lbl = self.state_label(root)
        btn = Button(root, text="CLEAR", font=("arial", 14, "bold"), command=self.board_clear)
        btn.grid(row=3, column=2)
    
    def state_label(self, frame):
        lbl = Label(frame, text="Play Game", font=("arial", 20, "bold"))
        lbl.grid(row=3, column=0, columnspan=2)
        return lbl 
    
    def board_clear(self):
        for row in range(3):
            for col in range(3):
                self.board[row][col].config(state = NORMAL, 
                                            text = " ",
                                            bg="papaya whip")
        self.xFirst()
               
    def button(self, frame):
        btn=Button(frame, text=" ", 
               padx=1, bg="papaya whip", 
               width=3, font=('arial',30,"bold"),
               relief="sunken", bd=5)
        return btn
    
    def xFirst(self):
        r_board = {1:"0,0", 2:"0,1", 3:"0,2",
                   4:"1,0", 5:"1,1", 6:"1,2",
                   7:"2,0", 8:"2,1", 9:"2,2", 
                   }
        if (self.board[0][0]["text"] == self.board[0][1]["text"] == self.board[0][2]["text"] == " ") and \
            (self.board[1][0]["text"] == self.board[1][1]["text"] == self.board[1][2]["text"] ==" ") and \
            (self.board[2][0]["text"] == self.board[2][1]["text"] == self.board[2][2]["text"] == " "):
                r_pos = random.randint(1,9)
                row, col = r_board[r_pos].split(",")
                self.board[int(row)][int(col)]["text"] = "X"
                self.board[int(row)][int(col)].config(state=DISABLED, disabledforeground="deep sky blue")
    
    def win(self, mark):
        if (self.board[0][0]["text"] == self.board[0][1]["text"] == self.board[0][2]["text"] == mark):
            return True
        elif (self.board[1][0]["text"] == self.board[1][1]["text"] == self.board[1][2]["text"] == mark):
            return True
        elif (self.board[2][0]["text"] == self.board[2][1]["text"] == self.board[2][2]["text"] == mark):
            return True
        elif (self.board[0][0]["text"] == self.board[1][0]["text"] == self.board[2][0]["text"] == mark):
            return True
        elif (self.board[0][1]["text"] == self.board[1][1]["text"] == self.board[2][1]["text"] == mark):
            return True
        elif (self.board[0][2]["text"] == self.board[1][2]["text"] == self.board[2][2]["text"] == mark):
            return True
        elif (self.board[0][0]["text"] == self.board[1][1]["text"] == self.board[2][2]["text"] == mark):
            return True
        elif (self.board[2][0]["text"] == self.board[1][1]["text"] == self.board[0][2]["text"] == mark):
            return True
        else:
            return False
    
    def draw(self):
        for row in range(3):
            for col in range(3):
                if self.board[row][col]["text"] == " " :
                    return False
        return True

    def game_over(self):
        for row in range(3):
            for col in range(3):
                self.board[row][col]["state"] = DISABLED 
    
    def threading(self) :
        ai_thread = Thread(target=self.com)
        ai_thread.start()
            
    def play(self, row, col):
        o_player.select_block(row, col)
        if self.win("O") :
            print("O win")
            self.lbl.config(text = "O win", font=("arial", 20, "bold"))                
            self.game_over()
        elif self.draw() :
            print("Draw")
            self.lbl.config(text = "Draw", font=("arial", 20, "bold"))
        else :
            self.lbl.config(text = "Play Game", font=("arial", 20, "bold"))
            
        self.threading()
    
    def com(self): 
        bestScore = -800
        score = 0
        bestMove_row = 0
        bestMove_col = 0     
        for row in range(3):
            for col in range(3):
                if self.board[row][col]["text"] == " ":
                    x_player.select_block(row, col)                    
                    self.board[row][col]["disabledforeground"] = "black"
                    score = self.minimax(self.board, False)                    
                    self.board[row][col]["text"] = " "
                    self.board[row][col].config(state=NORMAL)
                    if score > bestScore :
                        bestScore = score
                        bestMove_row = row
                        bestMove_col  =col
        x_player.select_block(bestMove_row, bestMove_col)        
        
        if self.win("X") :
            print("X win")
            self.lbl.config(text = "X win", font=("arial", 20, "bold"))                
            self.game_over()
        elif self.draw() :
            print("Draw")
            self.lbl.config(text = "Draw", font=("arial", 20, "bold"))
        else :
            self.lbl.config(text = "Play Game", font=("arial", 20, "bold"))
        
    def minimax(self, board, isMaximizing):
        #self.lbl["text"] = "Please wait, AI is choosing."
        self.lbl.config(text = "Please wait, Ai is choosing.", font=("arial", 10, "bold"))
        
        if self.win("X"):
            return 1
        elif self.win("O"):
            return -1
        elif self.draw():
            return 0
    
        if isMaximizing :
            bestScore = -800
            score = 0 
            for row in range(3):
                for col in range(3):
                    if self.board[row][col]["text"] ==" ":
                        self.board[row][col]["text"] ="X"
                        score = self.minimax(board, False)
                        self.board[row][col]["text"] =" "
                        self.board[row][col].config(state=NORMAL)
                    if score > bestScore:
                        bestScore = score
                        print("X : ", bestScore)
            return bestScore
        else:
            bestScore = 800
            score = 0 
            for row in range(3):
                for col in range(3):
                    if self.board[row][col]["text"] ==" ":
                        self.board[row][col]["text"] = "O"
                        score = self.minimax(board, True)
                        self.board[row][col]["text"] =" "
                        self.board[row][col].config(state=NORMAL)
                    if score < bestScore:
                        bestScore = score
                        print("O : ", bestScore)
            return bestScore               
################################################################################################################
class Player():
    player =""
    def __init__(self, player):
       self.player = player   
     
    def select_block(self, row, col):
        Board.board[row][col]["text"] = self.player        
        # player color : X - deep sky blue / O - lawn green
        if self.player == "X":
                Board.board[row][col].config(state=DISABLED, disabledforeground="deep sky blue")
        elif self.player == "O":
            Board.board[row][col].config(state=DISABLED, disabledforeground="lawn green")
################################################################################################################
                    
# main - begin
root = Tk()
root.title("Tic Tac Toe")
root.resizable(False, False)

board = Board()
x_player = Player("X")
o_player = Player("O")
board.xFirst()

root.mainloop()
# main - end
```  

* X의 처음 선택은 랜덤, 비워있는 칸이 많을 수록 모든 경우의 수를 계산하여 시간이 걸림.  
* 추가할 것 : 알파베타 가지치기를 이용하여 재귀함수의 횟수 줄이기

