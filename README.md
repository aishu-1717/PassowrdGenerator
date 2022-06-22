# PassowrdGenerator
import random

def randomCase(word: str) -> str:
    res = ''
    choices = True, False
    for c in word:
        if random.choice(choices):
            res += c.swapcase()
        else:
            res += c
    return res

def addNums(word: str) -> str:
    res = ''
    choices = True, False
    for c in word:
        if random.choice(choices):
            res += str(random.randint(0, 9))
        res += c
    return res


def generatePassword(words: list[str]) -> str:
    res = '' 
    max_words = 3
    for _ in range(max_words):
        res +=  random.choice(words)
    
    return addNums(res)

def isStrongPassword(password: str):
    return len(password) > 8 and password.isalnum()



def main():
    words = input('Enter words (seperated by space): ').split()
    password = generatePassword(words)

    if isStrongPassword(password):
        print(password, 'is a strong password')
    else:
        print(password, 'is not a strong password')
    
    with open('password.txt', 'a') as f:
        f.write(password + '\n')

if __name__ == '__main__':
    main()
