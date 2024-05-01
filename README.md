# Criando-um-Sistema-Bancario-com-Python
Desafio de Projetos Dio

menu = """
[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair
=> """

saldo = 0
limite = 1000
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 2

while True:
    opcao = input(menu).lower()

    if opcao == "d":
        valor = float(input("Informe o valor do depósito: "))
        if valor > 0:
            saldo += valor
            extrato += f'Depósito: R$ {valor:.2f}\n'
        else:
            print("Operação falhou! O valor informado é inválido. Tente novamente!")

    elif opcao == 's':
        valor = float(input("Informe o valor do saque: "))
        if valor > saldo:
            print("Operação falhou! Você não possui saldo suficiente.")
        elif valor > limite:
            print("Operação falhou! O valor do saque excedeu o limite.")
        elif numero_saques >= LIMITE_SAQUES:
            print("Operação falhou! Número de saques foi excedido.")
        elif valor > 0:
            saldo -= valor
            extrato += f'Saque: R$ {valor:.2f}\n'
            numero_saques += 1
        else:
            print("Operação falhou! O valor informado é inválido.")

    elif opcao == "e":
        print("\n=============EXTRATO==============")
        print("Não foram realizadas movimentações." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("==================================")

    elif opcao == "q":
        break

    else:
        print("Operação inválida, por favor selecione novamente a operação desejada.")
