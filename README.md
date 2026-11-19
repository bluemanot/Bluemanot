#!/usr/bin/env python3
import sys
R='\033[38;5;213m';RL='\033[38;5;219m';RD='\033[38;5;169m';RS='\033[0m';B='\033[1m'
def clear():print("\033[2J\033[H",end="")
def header():
    print(f"{RL}{B}")
    print("  ╭─────────────────────────╮")
    print("  │   ♡ Calculadora Rosa ♡  │")
    print("  ╰─────────────────────────╯")
    print(f"{RS}")
def menu():
    print(f"{R}  [1] + Soma    [2] - Sub")
    print(f"  [3] × Mult    [4] ÷ Div")
    print(f"  [5] ^ Pot     [6] √ Raiz")
    print(f"  [0] Sair{RS}\n")
def get_num(msg):
    while True:
        try:return float(input(f"{RD}  {msg}: {RS}"))
        except ValueError:print(f"{RL}  ⚠ Número inválido{RS}")
def calc():
    while True:
        clear();header();menu()
        op=input(f"{RD}  Opção: {RS}")
        if op=='0':
            print(f"\n{RL}  ♡ Até logo! ♡{RS}\n");break
        if op=='6':
            n1=get_num("Número")
            if n1<0:print(f"{RL}  ⚠ Raiz de negativo? Não!{RS}")
            else:print(f"\n{R}  √{n1} = {n1**0.5:.2f}{RS}")
        elif op in '12345':
            n1=get_num("1º número");n2=get_num("2º número")
            ops={'1':('+',n1+n2),'2':('-',n1-n2),'3':('×',n1*n2),'4':('÷',None),'5':('^',n1**n2)}
            if op=='4':
                if n2==0:print(f"{RL}  ⚠ Divisão por zero!{RS}")
                else:print(f"\n{R}  {n1} ÷ {n2} = {n1/n2:.2f}{RS}")
            else:
                simb,r=ops[op];print(f"\n{R}  {n1} {simb} {n2} = {r:.2f}{RS}")
        else:print(f"{RL}  ⚠ Opção inválida{RS}")
        input(f"\n{RD}  Enter para continuar...{RS}")
if __name__=="__main__":
    try:calc()
    except KeyboardInterrupt:print(f"\n{RL}  ♡ Bye! ♡{RS}\n");sys.exit(0)


🍩comandos termos🍩:
pkg install python
nano calc.py