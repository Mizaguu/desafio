menu = """
[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

=> """

saldo = 0
limite = 500
estrato = ""
numero_saques = 0
LIMITE_SAQUES = 3

while True:

    opcao = input(menu)

    if opcao == "d":
        valor_deposito = float(input("Digite o valor do depósito: R$ "))
        if valor_deposito > 0:
            saldo += valor_deposito
            estrato += f"\nDepósito: R$ {valor_deposito:.2f}"
            print(f"Depósito realizado com sucesso! Saldo atual: R$ {saldo:.2f}")
        else:
            print("Valor inválido. O valor do depósito deve ser positivo.")

    elif opcao == "s":
        valor_saque = float(input("Digite o valor do saque: R$ "))
        if valor_saque > 0 and numero_saques < LIMITE_SAQUES and valor_saque <= saldo:
            saldo -= valor_saque
            estrato += f"\nSaque: R$ {valor_saque:.2f}"
            numero_saques += 1
            print(f"Saque realizado com sucesso! Saldo atual: R$ {saldo:.2f}")
        elif numero_saques >= LIMITE_SAQUES:
            print(f"Limite de saques diários atingido ({LIMITE_SAQUES}). Tente novamente amanhã.")
        elif valor_saque > saldo:
            print(f"Saldo insuficiente. Saldo atual: R$ {saldo:.2f}")
        else:
            print("Valor inválido. O valor do saque deve ser positivo.")

    elif opcao == "e":
        print(f"\n--- Extrato ---")
        print(f"Saldo: R$ {saldo:.2f}")
        print(estrato)
        print(f"Saques realizados hoje: {numero_saques}/{LIMITE_SAQUES}")

    elif opcao == "q":
        print("Obrigado por utilizar nosso banco!")
        break

    else:
        print("Operação inválida, por favor selecione novamente a operação desejada.")


