# Python
Trabalho em Python
from datetime import datetime
data_e_hora_atuais = datetime.now()
data_e_hora_em_texto = data_e_hora_atuais.strftime('%d/%m/%Y')
print(data_e_hora_em_texto,"/ BEM VINDO!")
print('''Digite 0 para adicionar uma vaca para ordenha.
Digite 1 para ver número de brincos já ordenhadas.
Digite 2 para buscar vacas já ordenhadas.
Digite 3 para excluir vaca da ordenha.
Digite 4 para sair.''')

# VALIDAR O MENU
def ler(text):
    while True:
        n1 = str(input(text))
        if n1.isnumeric():
            valor = int(n1)
            if valor == 0 or valor == 1 or valor == 2 or valor == 3 or valor == 4:
                break
            else:
                print('Escolha uma opção válida!')
        else:
            print('Digite um número válido!')
    return valor

def menu():
    lista.sort()
    n = ler('Digite um número para iniciar: ')
    if n == 0:
        adicionar()
    if n == 1:
        quantidade()
    if n == 2:
        num = ler2('Digite o código do brinco: ')
        busc = buscaBinaria(lista, num)
        if busc:
            print(f"código {num} ja ordenhada")
            print('''MENU PRINCIPAL               
            Digite 0 para adicionar uma vaca para ordenha.
            Digite 1 para ver número de brincos já ordenhados.
            Digite 2 para buscar vacas já ordenhadas.
            Digite 3 para excluir vaca da ordenha.
            Digite 4 para sair.''')

            menu()
        else:
            print(f"Não foi encontrada ordenha com o código {num}")
            while True:
                resp = (input(f'Deseja adicionar ordenha com este código? {num} [S/N]')).upper()[0]
                if resp in 'N':
                    menu()
                    break
                elif resp in 'S':
                    if num not in lista:
                        lista.append(num)

                        print('código adicionado com sucesso!...')

                        print('''MENU PRINCIPAL               
                        Digite 0 para adicionar uma vaca para ordenha.
                        Digite 1 para ver número de brincos já ordenhadas.
                        Digite 2 para buscar vacas já ordenhadas.
                        Digite 3 para excluir vaca da ordenha.
                        Digite 4 para sair.''')

                        menu()
                else:
                    resposta(resp)
    if n == 3:
        excluir()

# FUNÇÃO ADICIONAR
def ler2(text):
    while True:
        n1 = str(input(text))
        if n1.isnumeric():
            valor1 = int(n1)
            break
        else:
            print('Digite um número inteiro válido.')
    return valor1


# DIGITE S OU N
def resposta(res):
    p = res
    if isinstance(p, str):
        print('Digite S para Sim e N para Não')


# FUNÇÃO PARA ADICIONAR
def adicionar():
    while True:
        add = ler2('Digite o código de brinco para adicionar: ')
        if add not in lista:
            lista.append(add)
            print('Código da ordenha adicionado com sucesso...')
        else:
            print('O código já esta na lista!')
        while True:
            resp = (input('Deseja adicionar outro código para ordenha? [S/N]')).upper()[0]
            if resp in 'N':
                menu()
                break
            elif resp in 'S':
                break
            else:
                resposta(resp)
        if resp in 'N':
            break


# SABER QUAIS ORDENHAS FORAM ADICIONADAS

def quantidade():
    for i in lista:

        print(f'  {i}', end=" / ")

    print(f'\nTotal ordenhadas:{len(lista)} ')
    while True:
        resp = (input('Digite S para Voltar ao Menu Principal ou N para fechar o programa [S/N]: ')).upper()[0]
        if resp in 'NS':
            print('''MENU PRINCIPAL               
            Digite 0 para adicionar uma vaca para ordenha.
            Digite 1 para ver número de brincos já ordenhados.
            Digite 2 para buscar vacas já ordenhadas.
            Digite 3 para excluir vaca da ordenha.
            Digite 4 para sair.''')
            break
        else:
            resposta(resp)
    if resp in 'S':
        menu()

# BUSCA ORDENHA BINARIO
def buscaBinaria(lists, item):
    prim = 0
    ult = len(lists) - 1
    found = False

    while prim <= ult and not found:
        meio = (prim + ult) // 2
        if lists[meio] == item:
            found = True
        else:
            if item < lists[meio]:
                ult = meio - 1
            else:
                prim = meio + 1
    return found


# EXCLUIR ORDENHA DO SISTEMA
def excluir():
    number = ler2('Digite o código do brinco que deseja remover: ')
    if number in lista:
        lista.remove(number)
        print('Código removido com sucesso')
        print('''MENU PRINCIPAL               
        Digite 0 para adicionar uma vaca para ordenha.
        Digite 1 para ver número de brincos já ordenhadas.
        Digite 2 para buscar vacas já ordenhadas.
        Digite 3 para excluir vaca da ordenha.
        Digite 4 para sair.''')

        menu()
    else:
        print('Não foi possível remover! \nBrinco não encontrado')
        r = ler2("Digite 10 para voltar,\nOu o número do brinco que deseja remover: ")
        if r == 10:
           menu()
        else:
            excluir()


lista = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
menu()
print('FIM!')
