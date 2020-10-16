# Formas-de-Pagamento
# Esse programa tem 5 opções de pagamento Dinheiro/Cheque, Cartão/Credito/Debito, Cartão 2x ou mais e Saldo devedor

cx = 'Formas de pagamento'
print('-' * 45)
val = int(input('Qual o valor do produto? '))
print('-' * 45)

print('-' * 45)
print(f'{cx:^45}')
print('-' * 45)

print('[ 1 ]Á vista Dinheiro/Cheque\n'
               '[ 2 ]Cartão/Crédito/Débito\n'
               '[ 3 ]2x no cartão\n'
               '[ 4 ]2x ou mais no cartão\n'
      '[ 5 ]Saldo devedor')

print('-' * 45)
op = int(input('Escolha uma opção acima: '))
print('-' * 45)


if op < 1 or op > 6:
    while True:
        op = int(input('Escolha uma opção acima: '))
        if op > 0 and op < 6:
            break
        else:
            pass

if op == 1:
    print(f'\033[34m{val} pago no Cartão/Cheque dá um total de R${val * 0.85} com 15% de desconto\033[m')
elif op == 2:
    print(f'\033[34m{val} pago no Cartão/Crédito/Débiro dá um total de R${val * 0.90} com %10 de desconto\033[m')
elif op == 3:
    print(f'\033[34m{val} em 2x no cartão dá um total de R${val / 2} por mês\033[m')
elif op == 4:
    par = int(input('Em quantas parcelas deseja pagar?'))
    if par > 1:
        print(f'\033[34m{val} Em {par}x dá um total de R${val / par} por mês\033[m')
    elif par < 2:
        while True:
            par = int(input('\033[31mMin de 2x.Em quantas parcelas deseja pagar?\033[m'))
            if par > 1:
                print(f'\033[34m{val} em {par}x dá um total de R${val / par} por mês\033[m')
                break
            else:
                pass
elif op == 5:

    por = int(input('Qual o valor dos juros?% '))
    par = int(input('Quantas parcelas? '))
    print('-' * 45)

    c = 0
    val1 = val
    p = par
    s = 0
    cont = 0

    for x in range(1, par + 1):
        cont += 1
        val1 *= (1 + por / 100)
        calc = val1 / p
        print(f'{cont}° parcela: \033[4m{calc:.2f}\033[m')
        val1 = val1 - calc
        s += calc
        p -= 1

    print(f'{val}R$ com juros dá um total de \033[4m{s + val:.2f}\033[m\n'
          f'Total de juros: \033[4m{s - val:.2f}\033[m')
    print('-' * 45)
