# SIMULADO
Questoes do Simulado1
def calcular_custo_vestibular_indigena(qtd_passageiros, tipo_transporte):
    if tipo_transporte == 'C':
        preco_por_pessoa = 60.00
        duracao_viagem = 6
        capacidade_transporte = 6
    elif tipo_transporte == 'V':
        preco_por_pessoa = 120.00
        duracao_viagem = 2
        capacidade_transporte = 8
    elif tipo_transporte == 'B':
        preco_por_pessoa = 40.00
        duracao_viagem = None 
        capacidade_transporte = 200
    else:
        return "Tipo de transporte inválido."

    custo_total = 0.00

    if tipo_transporte == 'B':
        if qtd_passageiros > capacidade_transporte:
            return "Quantidade de passageiros excede a capacidade do barco."
        else:
            custo_total = qtd_passageiros * preco_por_pessoa
    else:
        if qtd_passageiros > capacidade_transporte:
            viagens_necessarias = qtd_passageiros / capacidade_transporte
            viagens_necessarias = int(viagens_necessarias) + 1 
            custo_total = viagens_necessarias * capacidade_transporte * preco_por_pessoa
        else:
            custo_total = qtd_passageiros * preco_por_pessoa

    # Verifica se é necessário acrescentar o custo de hospedagem e alimentação
    if tipo_transporte != 'B' and duracao_viagem is not None and duracao_viagem > 4:
        custo_total += 65.00 * qtd_passageiros

    return f"Passageiros: {qtd_passageiros}\nTipo de transporte: {tipo_transporte}\nTotal a ser gasto: R$ {custo_total:.2f}"

entrada = input("Digite a quantidade de passageiros e o tipo de transporte (Exemplo: 4 C): ")
qtd_passageiros, tipo_transporte = entrada.split()
qtd_passageiros = int(qtd_passageiros)

resultado = calcular_custo_vestibular_indigena(qtd_passageiros, tipo_transporte)
print(resultado)
