# Python Lesson09：项目01~和平精英

## 游戏案例信息

![](image/1gcogjgmlc.png "")

## 以代码的方式来实现游戏案例

代码实现如下所示：

```React JSX
import random #导入需要使用的文件

print("------欢饮来打和平精英训练岛------")  # 先向玩家打招呼

solider_name = input(print("特种兵请留下名字吧： "))  # 要求输入名字

#我们在这里封装一个函数
def isHit(n, score):
  recod = 0
  for i in range(30):
    r1 = random.randint(1, n)
    r2 = random.randint(1, n)
    if r1 == r2:
      recod += score

  return recod

while True:

  choice = input(print("请输入： 1.室内靶场 2.大乱斗"))  # 要求用户选择模式
  

  # 判断用户输入的数字
  if choice == "1":
    print("请坐稳，传送点马上带你进入室内靶场")

    guns = ["AK47", "98K", "VSS", "AUG", "M726"]  # 用户需要选择使用的枪支
    for gun in guns:
      print(gun)
    gun = input(print("请选择枪支： "))

    levels = ["Easy", "Medium", "Difficult"]  # 用户需要选择游戏的难度
    for level in levels:
      print(level)
    level = input(print("请选择难度"))

    # 接着我们可以调用这个封装的函数
    # 注：Python会一行一行的来执行代码，所以被调用的函数需要在调用这个函数之前
    if level == "Easy":
      score = isHit(10, 5)
    elif level == "Normal":
      score = isHit(20, 10)
    elif level == "Difficult":
      score = isHit(30, 20)
    else:
      print("{}请选择正确的难度等级".format(solider_name))
      break

    print("训练完毕！{}使用{}抢在{}难度之下获得了{}的分数".format(solider_name, gun, level, score))
    break

  elif choice == "2":
    print("请做好准备，你马上就要变成一只可爱的光子鸡！")
    print("{}已经变成了一只小鸡仔，而且还有一把枪，射击模式开始！")
    coins = 0  # 用来表示金币
    level = 1  # 用来表示等级
    count = 0  # 击中敌人的个数

    while True:
      r = random.randint(1, 20)
      if r % 5 == 0:
        print("恭喜你击中了一个敌人")
        coins += r * level
        count += 1
      # 4种等级，0-400，400-900，900-2000，2000以上
      if coins >= 0 and coins < 400:
        level = 1
      elif coins >= 400 and coins < 900:
        level = 2
      elif coins >= 900 and coins < 2000:
        level = 3
      elif coins >= 2000:
        print("{}你已经是一个合格的特种兵了，请上战场吧！".format(solider_name))
        break
    break
  else:
    print("输入有误，请重新输入")
```


