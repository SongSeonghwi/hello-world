import random

# 生成一个1-100之间的随机整数
number = random.randint(1, 100)

# 用于记录玩家猜测的次数
guesses = 0

# 游戏循环
while True:
    # 从玩家获取猜测
    guess = int(input("请猜测一个1-100之间的整数："))

    # 增加猜测次数
    guesses += 1

    # 判断猜测结果
    if guess < number:
        print("你猜的数字太小了！")
    elif guess > number:
        print("你猜的数字太大了！")
    else:
        print("恭喜你猜对了！")
        print("你一共猜了", guesses, "次。")
        break

