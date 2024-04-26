import pygame, simpleGE, random
class Intro(simpleGE.Scene):
    def __init__(self):
        super().__init__()
        
        self.status = "quit"
        
        
        self.lblInstructions = simpleGE.MultiLabel()
        self.lblInstructions.textLines = [
            "Barfight",
            "Gain Strength Levels",
            "Defeat All Enemies"]
        self.lblInstructions.center = (320, 240)
        self.lblInstructions.size = (400, 100)
        

        self.btnPlay = simpleGE.Button()
        self.btnPlay.center = (150, 400)
        self.btnPlay.text = "Play"
        
        self.btnQuit = simpleGE.Button()
        self.btnQuit.center = (500, 400)
        self.btnQuit.text = "Quit"
        
        self.sprites = [
            self.lblInstructions,
            self.btnPlay,
            self.btnQuit
            ]

    def process(self):
        if self.btnPlay.clicked:
            self.status = "play"
            self.stop()
        if self.btnQuit.clicked:
            self.status = "quit"
            self.stop()
                    


class Hero(simpleGE.Sprite):
    def __init__(self, scene):
        super().__init__(scene)
        self.setImage("walking s0000.bmp")
        #self.colorRect("blue", (25, 25))
        self.loadPics()
        self.copyImage(self.imgList[0][0])
        self.moveSpeed = 5
    
    def loadPics(self):
        fileBase = [
            "walking e0000",
            
            "walking n0000",
            
            "walking w0000",
            
            "walking s0000"
            
        ]

        self.imgList = []
        for dir in range(len(fileBase)):
            tempList = []
            tempFile = fileBase[dir]
            for frame in range(8):
                imgName = f"{tempFile}.bmp"
                tmpImg = pygame.image.load(imgName)
                tmpImg.convert()
                tranColor = tmpImg.get_at((0,0))
                tmpImg.set_colorkey(tranColor)
                tempList.append(tmpImg)
            self.imgList.append(tempList)
    
    def process(self):
        if self.isKeyPressed(pygame.K_LEFT):
            self.x -= self.moveSpeed
            #self.loadPics("walking w0000")
        if self.isKeyPressed(pygame.K_RIGHT):
            self.x += self.moveSpeed
            #self.loadPics("walking e0000")
        if self.isKeyPressed(pygame.K_UP):
            self.y -= self.moveSpeed
            #self.loadPics("walking n0000")
        if self.isKeyPressed(pygame.K_DOWN):
            self.y += self.moveSpeed
            #self.loadPics("walking s0000")

    
            
class Enemy(simpleGE.Sprite):
    def __init__(self, scene):
        super().__init__(scene)
        self.setImage("enemywalking s00000.bmp")
        self.loadPics()
        self.copyImage(self.imgList[0][0])
        self.x = random.randint(0, self.screenWidth)
        self.y = random.randint(0, self.screenWidth)
        self. moveSpeed = 5
        
    def reset(self):
        
            
        
        
            self.x = random.randint(0,self.screenWidth)
        
        
            self.y = random.randint(0,self.screenWidth)
        
    def loadPics(self):
        fileBase = [
            "enemywalking e00000",
            #"enemywalking ne000",
            "enemywalking n00000",
            #"enemywalking nw000",
            "enemywalking w00000",
            #"enemywalking sw000",
            "enemywalking s00000",
            #"enemywalking se000"
        ]

        self.imgList = []
        for dir in range(len(fileBase)):
            tempList = []
            tempFile = fileBase[dir]
            for frame in range(8):
                imgName = f"{tempFile}.bmp"
                tmpImg = pygame.image.load(imgName)
                tmpImg.convert()
                tranColor = tmpImg.get_at((0,0))
                tmpImg.set_colorkey(tranColor)
                tempList.append(tmpImg)
            self.imgList.append(tempList)


        
        
class Game(simpleGE.Scene):
    def __init__(self):
        super().__init__()
        self.setImage("bar_background.png")
        self.hero = Hero(self)
        self.enemy = Enemy(self)
        self.lblInstructions = simpleGE.MultiLabel()
        self.lblInstructions.textLines = ["You Win!"]
        self.lblInstructions.center = (320, 240)
        self.lblInstructions.size = (400, 100)
        
        #self.numEnemies = 3
        #self.enemy = []
        #for i in range(self.numEnemies):
            #self.enemy.append
        self.score = 5
        self.enemyScore = 1
        #self.enemyScore = self.score 
        #if enemyScore > self.score:
            
            #self.quit
        self.lblScore = simpleGE.Label()
        self.lblScore.center = (150, 100)
        self.lblScore.text = f"Strength: {self.score}"
        self.lblEnemyScore = simpleGE.Label()
        self.lblEnemyScore.center = (450, 100)
        self.lblEnemyScore.text = f"Strength: {self.enemyScore}"
        self.sprites = [self.hero]
        self.sprites = [self.enemy]
        self.sprites = [self.lblScore]
        self.sprites = [self.lblEnemyScore]
        #self.sprites = [self.lblInstructions]
        #self.numEnemy = 3 
        
        self.sprites = [
            self.lblScore,
            self.hero,
            self.enemy,
            self.lblEnemyScore
            ]
    def process(self):
        #for enemy in self.enemy:
            import random
            randomInt = random.randint(1,10)
            self.lblInstructions = simpleGE.MultiLabel()
            self.lblInstructions.textLines = ["You Win!"]
            self.lblInstructions.center = (320, 240)
            self.lblInstructions.size = (400, 100)
            if self.enemy.collidesWith(self.hero):
                if self.score < self.enemyScore:
                    quit()
                self.enemyScore = randomInt
                
                self.lblEnemyScore.text = f"Strength: {self.enemyScore}"
                self.enemy.reset()
                #import random
                if self.score >= 10:
                    self.sprites = [self.lblInstructions]
                else:
                    self.score += 1
                
                #randomInt = random.randint(1,10)
                #self.lblEnemyScore.text = f"Strength: {self.enemyScore}"
                #self.enemyScore += randomInt
                #self.lblEnemyScore.text = f"Strength: {self.enemyScore}"
                
                self.lblScore.text = f"Strength: {self.score}"
                
                
                        
           
            
def main():
        keepGoing = True
        
        while keepGoing:
            intro = Intro()
            intro.start()
            
            if intro.status == "quit":
                keepGoing = False
            else:
                game = Game()
                game.start()
                
if __name__ == "__main__":
    main()
