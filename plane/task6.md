# 完成飞机大战游戏设计
## 【作业要求】

- 自己敲一遍源代码，对自己负责
- 写出代码的整体框架
- 写出每个类及每个函数的作用
- 整理代码实现过程中遇到的问题
- 实验结果截图

# 飞机大战框架
首先设置游戏界面的大小、标题、背景图片、飞机图片（正常、爆炸）、子弹图片；然后设置两个list，分别存储敌机和被击毁的飞机；然后初始化分数、射击频率、敌机移动频率，并设置游戏循环帧率；然后进入游戏的主循环部分；然后在gameover后显示最终得分；最后处理游戏退出。     

在游戏的主循环部分主要包括以下部分：    
- （1）按一定频率发射子弹
- （2）按一定频率生成敌机
- （3）移动子弹
- （4）移动敌机
- （5）敌机与玩家飞机相撞处理方法
- （6）敌机被子弹击中处理方法
- （7）一系列绘制、显示的方法，包括：绘制背景、绘制玩家飞机、显示子弹、显示敌机、绘制得分、更新屏幕
- （9）处理退出游戏。      一共个建立了3个类，分别是：（1）子弹类；（2）玩家飞机类；（3）敌机类


# 设置游戏屏幕大小
SCREEN_WIDTH = 480
SCREEN_HEIGHT = 800

# 类和函数

**子弹类**

继承自pygame.sprite.Sprite类，构造函数__init__()定义了子弹的图片、位置和速度，函数move()定义了子弹的移动方式。
```python
class Bullet(pygame.sprite.Sprite):
    def __init__(self, bullet_img, init_pos):
        pygame.sprite.Sprite.__init__(self)
        self.image = bullet_img
        self.rect = self.image.get_rect()
        self.rect.midbottom = init_pos
        self.speed = 10

    def move(self):
        self.rect.top -= self.speed
```
**玩家类**

继承自pygame.sprite.Sprite类，构造函数__init__()中调用了父类的构造函数，定义了玩家的飞机的图片、位置、速度和是否被击中等基本属性，函数shoot()定义了发射子弹的方法，函数moveUp()、moveDown()、moveLeft()和moveRight()分别定义了向上、向下、向左、向右移动的方法。
```python
class Player(pygame.sprite.Sprite):
    def __init__(self, plane_img, player_rect, init_pos):
        pygame.sprite.Sprite.__init__(self)
        self.image = []                                 # 用来存储玩家飞机图片的列表
        for i in range(len(player_rect)):
            self.image.append(plane_img.subsurface(player_rect[i]).convert_alpha())
        self.rect = player_rect[0]                      # 初始化图片所在的矩形
        self.rect.topleft = init_pos                    # 初始化矩形的左上角坐标
        self.speed = 8                                  # 初始化玩家飞机速度，这里是一个确定的值
        self.bullets = pygame.sprite.Group()            # 玩家飞机所发射的子弹的集合
        self.is_hit = False                             # 玩家是否被击中

    # 发射子弹
    def shoot(self, bullet_img):
        bullet = Bullet(bullet_img, self.rect.midtop)
        self.bullets.add(bullet)

    # 向上移动，需要判断边界
    def moveUp(self):
        if self.rect.top <= 0:
            self.rect.top = 0
        else:
            self.rect.top -= self.speed

    # 向下移动，需要判断边界
    def moveDown(self):
        if self.rect.top >= SCREEN_HEIGHT - self.rect.height:
            self.rect.top = SCREEN_HEIGHT - self.rect.height
        else:
            self.rect.top += self.speed

    # 向左移动，需要判断边界
    def moveLeft(self):
        if self.rect.left <= 0:
            self.rect.left = 0
        else:
            self.rect.left -= self.speed

    # 向右移动，需要判断边界
    def moveRight(self):
        if self.rect.left >= SCREEN_WIDTH - self.rect.width:
            self.rect.left = SCREEN_WIDTH - self.rect.width
        else:
            self.rect.left += self.speed
```
**敌机类**

继承自pygame.sprite.Sprite类，构造函数__init__()定义了敌机的图片、位置和速度等基本属性，函数move()定义了敌机移动的方法。
```python
class Enemy(pygame.sprite.Sprite):
    def __init__(self, enemy_img, enemy_down_imgs, init_pos):
        pygame.sprite.Sprite.__init__(self)
        self.image = enemy_img
        self.rect = self.image.get_rect()
        self.rect.topleft = init_pos
        self.down_imgs = enemy_down_imgs
        self.speed = 2

    # 敌机移动，边界判断及删除在游戏主循环里处理
    def move(self):
        self.rect.top += self.speed
```



# 代码实现问题
如直接在cmd中路径下运行`python plane.py`会出现如下错误


所以需要在`Anaconda Prompt (Anaconda3)`中运行python.py
才能成功

# 运行结果