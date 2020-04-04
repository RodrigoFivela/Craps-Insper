# Craps-Insper-Rodrigo Villela
import random
#Informações iniciais
print('Olá, Bem-Vindo ao Craps Insper!')
print ('Neste jogo, você começará com 120 fichas e as usará para apostar em qual será a soma do valor de dois dados que serão jogados.')
print('Vamos começar?')
fichas=120
print('O jogo é dividido em duas fases,')
print(' o Come Out, onde se define o tipo de aposta que fará e se realiza a primeira jogada de dados,')
print('e o Point, em que dependendo da aposta e do resultado anterior,os dados serão relançados para definir sua vitória ou derrota.')
print('Você poderá escolher entre quatro tipos de apostas:')
print('O"Pass Line Belt", onde o jogador ganha se a soma for de 7 ou 11 para ganhar, perde se for 2,3 ou 12, e se tirar um dos demais valores vai para o point, onde deve tirar o mesmo valor para ganhar.')
print('O Field, em que o jogador deve tirar 3,4,9,10 ou 11 pra ganhar o valor da aposta, 2 para gnhar o dobro ou 12 para ganhar o triplo. Perdendo tudo se tirar os demais valores.')
print('O Any Craps, onde para ganhar, é necessário tirar o valor de 2,3 ou 12 nos dados, ganhando assim, 7 vezes o valor da aposta.Perdendo se tirar os demais valores.' )
print('E por último, o Twelve, onde só é possível ganhar tirando o valor de 12 nos dados, ganhando 30 vezes o valor da sua aposta.')
#Dado que "Pass Line Belt" é o único só pode ser feito no início, sua programação é feita separada dos demais
Play=True
while Play:
    valor_aposta=0
    Won=False
    Lose=False
    Field=False
    Any_Cramps=False
    Twelve=False
    Escolha=False
    print('Você possui {0} fichas'.format(fichas))
    if fichas<=0:
        print('Acabaram suas fichas')
        Play=False
    else:
        print('Come Out')
        valor_aposta=int(input('Selecione o valor da sua aposta :'))
    if valor_aposta>fichas and fichas>0:
        print('Fichas insuficientes')
        valor_aposta=int(input('Selecione um valor de fichas que você possua :'))
    elif valor_aposta<=fichas and fichas>0:
        soma= random.randint(1,6)+random.randint(1,6)
        aposta=str(input('Selecione a sua aposta.Pressione "P" para "Pass line Belt", "F" para Field, "A" para Any Craps ou "T" para "Twelve":'))
        if aposta==str('P') or aposta==str('p'):
            print('Vamos Lá!')
            print('Jogando os dados...')
            print (soma)
            if soma==7 or soma==11:
                print('Você ganhou!')
                Won=True
            elif soma==2 or soma==3 or soma==12:
                print('Você perdeu.')
                Lose=True
            else:
                print('Vamos para o point')
                aposta=str(input('Deseja se manter no "Pass Line Belt" ou trocar para uma das demais? Use as mesmas letras de antes: '))
                if aposta==str('P') or aposta==str('p'):
                    print('Jogando os dados...')
                    soma2=random.randint(1,6)+random.randint(1,6)
                    print(soma2)
                    if soma2==soma:
                        print('Você ganhou!')
                        Won=True
                    else:
                        print('Você perdeu.')
                        Lose=True
                elif aposta==str('F') or aposta==str('f'):
                    Field=True
                elif aposta==str('A') or aposta==str('a'):
                    Any_Cramps=True
                elif aposta==str('T') or aposta==str('t'):
                    Twelve=True
        elif aposta==str('F') or aposta==str('f'):
            Field=True
        elif aposta==str('A') or aposta==str('a'):
            Any_Cramps=True
        elif aposta==str('T') or aposta==str('t'):
            Twelve=True
        if Field==True:
            print('Vamos lá')
            print (soma)
            if soma==5 or soma==6 or soma==7 or soma==8:
                print ('Você Perdeu')
                Lose=True
            elif soma==2:
                print('Você ganhou x2!')
                fichas=fichas+2*valor_aposta
            elif soma==12:
                print('Você ganhou x3!')
                fichas=fichas+3*valor_aposta
            else:
                print('Você ganhou!')
                Won=True
        if Any_Cramps==True:
            print('Vamos lá')
            print (soma)
            if soma==2 or soma==3 or soma==12:
                print('Você ganhou x7!')
                fichas=fichas+valor_aposta*7
            else:
                print('Você perdeu.')
                Lose=True
        if Twelve==True:
            print('Vamos lá')
            print(soma)
            if soma==12:
                print('Você ganhou x30!')
                fichas=fichas+30*valor_aposta
            else:
                print ('Você perdeu.')
                Lose=True
        if Won==True:
            fichas=fichas+valor_aposta
            Escolha=True
        if Lose==True:
            fichas=fichas-valor_aposta
            Escolha=True
        if Escolha==True:
            decisão=str(input('Deseja continuar jogando? Pressione S para sim ou N para não: '))
            if decisão==str('S') or decisão==str('s'):
                Play=True
            elif decisão==str('N') or decisão==('n'):
                Play=False
            else:
                print('Escolha inválida')
                Escolha=True
if Play==False:
    print('Fim de Jogo')
