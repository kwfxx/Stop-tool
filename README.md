
import time, random

# أكواد الألوان ANSI
colors = ["\033[31m", "\033[32m", "\033[33m", "\033[34m", "\033[35m", "\033[36m", "\033[37m"]
reset = "\033[0m"

hexchars = "0123456789abcdef"
b64 = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/"

last = time.time()
while True:
    # نص مشفر وهمي
    enc = "".join(random.choice(hexchars) for _ in range(random.randint(16, 32)))
    enc += "-" + "".join(random.choice(b64) for _ in range(random.randint(20, 44)))
    color = random.choice(colors)
    print(color + enc + reset)

    # طباعة ethan كل ثانية
    if time.time() - last >= 1.0:
        last = time.time()
        print(random.choice(colors) + "ethan" + reset)

    # سرعة الطباعة (يمكنك تعديلها)
    
