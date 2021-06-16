# Projekt_Text_Analyzator
import math

TEXTS = ['''
Situated about 10 miles west of Kemmerer, 
Fossil Butte is a ruggedly impressive 
topographic feature that rises sharply 
some 1000 feet above Twin Creek Valley 
to an elevation of more than 7500 feet 
above sea level. The butte is located just 
north of US 30N and the Union Pacific Railroad, 
which traverse the valley.''',

'''At the base of Fossil Butte are the bright 
red, purple, yellow and gray beds of the Wasatch 
Formation. Eroded portions of these horizontal 
beds slope gradually upward from the valley floor 
and steepen abruptly. Overlying them and extending 
to the top of the butte are the much steeper 
buff-to-white beds of the Green River Formation, 
which are about 300 feet thick.''',

'''The monument contains 8198 acres and protects 
a portion of the largest deposit of freshwater fish 
fossils in the world. The richest fossil fish deposits 
are found in multiple limestone layers, which lie some 
100 feet below the top of the butte. The fossils 
represent several varieties of perch, as well as 
other freshwater genera and herring similar to those 
in modern oceans. Other fish such as paddlefish, 
garpike and stingray are also present.'''
]

data = {'bob': '123', 'ann': 'pass123', 'mike': 'password123', 'liz': 'pass123'}
ODDELOVAC = ('=' *40)

print(ODDELOVAC)
print('PŘIHLAŠOVACÍ ÚDAJE')
print(ODDELOVAC)

# Dotaz na uživatelské jméno a heslo.
username = input('Zadej svoje uživatelské jméno: ').lower()
password = input('Zadej svoje uživatelské heslo: ')
print(ODDELOVAC)

# Kontrola správnosti zadaného jména a heslo.
if data.get(username) == password:
  print('Dobrý den', username, 'můžete pokračovat v anylýze textu.')
else:
  print('Neplatné přihlašovací údaje. Registrujte se nebo si zkontrolujte přihlašovací údaje.')
  exit()
print(ODDELOVAC)

#Výběr textu
TEXT = input('Zadejte číslo textu k analýze 1 - 3: ')
print(ODDELOVAC)
if TEXT.isnumeric():
  if int(TEXT) < 1 or int(TEXT) > 3:
     print('Pod tímto zadaným číslem žádný text neexistuje.')
  else: 
     print('Vámi vybraný text: ')
     exit()
if TEXT.isalpha():
    print('Pod tímto zadaným znakem žádný text neexistuje.')
    exit()
print(ODDELOVAC)     

 # Vypsání vybraného tetxu
Správný_index = int(TEXT) - 1
Vybraný_text = TEXTS[Správný_index]
print(Vybraný_text)
print(ODDELOVAC)


slova=Vybraný_text.split(" ")

print(f"Celkový počet znaků ve vybraném textu: {len(slova)}")

vycistena_slova = [slovo.strip(".,?,'\n'") for slovo in slova]
i=0
j=0
k=0
l=0
m=0
delkaslov={}

#print(vycistena_slova)

for A in vycistena_slova:
  if A[0].isupper():
    i=1+i
  elif A.isupper():
    j=1+j
  elif A.islower():
    k=1+k
  elif A.isnumeric():
    m=int(A)+m
    l=1+l
  delkaslov[len(A)]=delkaslov.get(len(A),0)+1


print(f"Celkový počet slov začínajících na velké pismeno: {i}")
print(f"Celkový počet slov psaných velkým písmen: {j}")
print(f"Celkový počet slov psaných malým písmem: {k}")
print(f"Celkový počet čísel v textu: {l}")
print(f"Suma všech čísel v textu: {m} ")

delka=max(delkaslov.values())
print(ODDELOVAC)
print("DÉLKA|"+ " "*math.floor(delka/2-4)+"VÝSKYT" + " "*math.ceil(delka/2-4) + "|POČET")
print(ODDELOVAC)


for p, q in sorted(delkaslov.items()):
    if p <10:
        print("", p , "|"+"*"*q+ " "*(delka - q) +"|", q )
    else:
        print(p, "|" + "*" * q + " " * (delka - q) + "|", q)
print(ODDELOVAC)
