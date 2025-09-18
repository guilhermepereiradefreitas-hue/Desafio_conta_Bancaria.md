menu = """ 

[1] Depositar
[2] Sacar
[3] Extrato
[4] Sair

=> """

saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3

while True:                                                                         #Loop infinito para o menu

    opcao = input(menu)                                                             #Pede a opção do usuário

    if opcao == "1": 
        valor = float(input("Informe o valor do depósito: "))                       #Pede o valor do depósito

        if valor > 0:                                                               #Verifica se o valor é positivo
            saldo += valor                                                          # Adiciona o valor ao saldo
            extrato += f"Depósito: R$ {valor:.2f}\n"                                # Adiciona o valor ao extrato
        else:
            print("Operação falhou! O valor informado é inválido.")

    elif opcao == "2":
        valor = float(input("Informe o valor do saque: "))                         #Pede o valor do saque

        excedeu_saldo = valor > saldo                                              #Verifica se o valor é maior que o saldo
        excedeu_limite = valor > limite                                            #Verifica se o valor é maior que o limite
        excedeu_saques = numero_saques >= LIMITE_SAQUES                            #Verifica se o número de saques é maior que o limite

        if excedeu_saldo:                                                          #Verifica se o valor é maior que o saldo
            print("Operação falhou! Você não tem saldo suficiente.")

        elif excedeu_limite:                                                       #Verifica se o valor é maior que o limite
            print("Operação falhou! O valor do saque excede o limite.")

        elif excedeu_saques:                                                       #Verifica se o número de saques é maior que o limite
            print("Operação falhou! Número máximo de saques diários excedido.")

        elif valor > 0:                                                            #Verifica se o valor é positivo
            saldo -= valor                                                         #Subtrai o valor do saldo
            extrato += f"Saque: R$ {valor:.2f}\n"                                  #Adiciona o valor ao extrato
            numero_saques += 1                                                     #Incrementa o número de saques

        else:
            print("Operação falhou! O valor informado é inválido.")

