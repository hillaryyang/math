import random
 
class pile:
    def __init__(self, start, end, weight):
        self.start = start
        self.end = end
        self.weight = weight
 
N = 4046
M = random.randint(2, 6069) # weight (X)
print(f"M = {M}")
arr = [0] * N
 
def generate():
    # generate random sequence of 1s and 2s, represents coins
    ind = random.sample(range(0, N - 1), int(N / 2))
    for i in ind:
        arr[i] = 1
    for i in range(0, N):
        if arr[i] == 0:
            arr[i] = 2
 
def weigh(w):
    # less than M grams -> false
    # at least M grams -> true
    weigh.count += 1
    return w >= M
 
def remove(start, end, w):
    for i in range(start, end + 1):
        w -= arr[i]
        if (weigh(w)): return w
        w += arr[i]
    return w
 
def solve():
    w = 0
    t = 0 # tipping number
    for i in range(0, N):
        w += arr[i]
        if (weigh(w)): 
            t = i
            break
 
    # print(f"w = {w}, t = {t}")
    if t > 2023: # know for certain there is at least one 1g coin
        return remove(0, t, w)
    
    elif t <= 2023:
        piles = [pile(0, t, w)]
        w1 = 0
        start1 = t + 1
 
        for i in range(t + 1, N):
            w1 += arr[i]
            if weigh(w1):
                # print(f"start = {start1}, end = {i}, weight = {w1}")
                if (i - start1 + 1 != t):
                    if (i - start1 + 1 > t): return remove(start1, i, w1)
                    else: return remove(0, t, w)
                piles.append(pile(start1, i, w1))
                w1 = 0
                start1 = i + 1
 
                if (i > 2023): break
        
        for p in piles:
            x = remove(p.start, p.end, p.weight)
            if (x < p.weight): return x
    
        return w
 
weigh.count = 0
generate()
 
# print(arr)
 
print(f"The weight is {solve()}")
print(f"The number of weighings performed was {weigh.count}")
