# GS2026.1 - Pensamento Computacional e Automação com Python

NOME_MISSAO = "Exploring the Space"
NOME_EQUIPE  = "Equipe dos Maneiros"

# Matriz principal: [temperatura, comunicacao, bateria, oxigenio, estabilidade]
dados_missao = [
    [23, 95, 91, 97, 93],   # Ciclo 1 — início da missão
    [28, 78, 74, 93, 82],   # Ciclo 2 — estabilização dos sistemas
    [33, 61, 55, 89, 67],   # Ciclo 3 — queda parcial de comunicação
    [37, 39, 35, 85, 52],   # Ciclo 4 — alerta de energia
    [41, 25, 17, 76, 32],   # Ciclo 5 — risco operacional
    [35, 52, 30, 81, 48],   # Ciclo 6 — tentativa de recuperação
]

areas_monitoradas = [
    "Temperatura interna",
    "Comunicação com a base",
    "Sistema de energia",
    "Suporte de oxigênio",
    "Estabilidade operacional",
]

# FUNÇÕES DE ANÁLISE POR ÁREA

def analisar_temperatura(valor):
    
    if valor < 18:
        return "ATENÇÃO", 1, "Temperatura abaixo do ideal"
    elif valor <= 30:
        return "NORMAL", 0, "Temperatura estável"
    elif valor <= 35:
        return "ATENÇÃO", 1, "Temperatura elevada"
    else:
        return "CRÍTICO", 2, "Risco de superaquecimento"


def analisar_comunicacao(valor):
    # Classifica a qualidade do sinal e retorna (status, pontos, mensagem)
    if valor < 30:
        return "CRÍTICO", 2, "Comunicação com a base em nível crítico"
    elif valor < 60:
        return "ATENÇÃO", 1, "Comunicação instável"
    else:
        return "NORMAL", 0, "Comunicação estável"


def analisar_bateria(valor):
    # Classifica o nível de bateria e retorna (status, pontos, mensagem)
    if valor < 20:
        return "CRÍTICO", 2, "Bateria em nível crítico"
    elif valor < 50:
        return "ATENÇÃO", 1, "Bateria abaixo do recomendado"
    else:
        return "NORMAL", 0, "Energia estável"


def analisar_oxigenio(valor):
    # Classifica o nível de oxigênio e retorna (status, pontos, mensagem).
    if valor < 80:
        return "CRÍTICO", 2, "Oxigênio em nível crítico"
    elif valor < 90:
        return "ATENÇÃO", 1, "Oxigênio abaixo do ideal"
    else:
        return "NORMAL", 0, "Oxigênio adequado"


def analisar_estabilidade(valor):
    # Classifica a estabilidade operacional e retorna (status, pontos, mensagem)
    if valor < 40:
        return "CRÍTICO", 2, "Estabilidade operacional crítica"
    elif valor < 70:
        return "ATENÇÃO", 1, "Estabilidade operacional reduzida"
    else:
        return "NORMAL", 0, "Estabilidade operacional adequada"


# FUNÇÃO: CLASSIFICAR CICLO

def classificar_ciclo(pontuacao):
    #Retorna a classificação textual do ciclo com base na pontuação
    if pontuacao <= 2:
        return "MISSÃO ESTÁVEL"
    elif pontuacao <= 5:
        return "MISSÃO EM ATENÇÃO"
    else:
        return "MISSÃO CRÍTICA"

# FUNÇÃO: GERAR RECOMENDAÇÃO

def gerar_recomendacao(resultados):
    #Recebe lista de (status, pontos, msg) de cada área do cicl e retorna uma recomendação automática.
    
    status_temp = resultados[0][0]
    status_com = resultados[1][0]
    status_bat = resultados[2][0]
    status_oxi = resultados[3][0]
    status_est= resultados[4][0]

    criticos = []
    if status_temp == "CRÍTICO":
        criticos.append("verificar controle térmico da missão")
    if status_com == "CRÍTICO":
        criticos.append("tentar restabelecer contato com a base")
    if status_bat == "CRÍTICO":
        criticos.append("ativar modo de economia de energia")
    if status_oxi == "CRÍTICO":
        criticos.append("acionar protocolo de suporte à vida")
    if status_est == "CRÍTICO":
        criticos.append("reduzir operações não essenciais")

    if len(criticos) >= 3:
        return "Ativar modo de segurança e priorizar suporte à vida, energia e comunicação."
    elif criticos:
        return "Recomendação: " + "; ".join(criticos).capitalize() + "."
    else:
        em_atencao = [s for s, _, _ in resultados if s == "ATENÇÃO"]
        if em_atencao:
            return "Monitorar sistemas em atenção e preparar plano de contingência."
        return "Manter operação normal e continuar monitoramento."

# FUNÇÃO: ANALISAR TENDÊNCIA

def analisar_tendencia(riscos):
    # Compara risco do primeiro e do último ciclo
    if riscos[-1] > riscos[0]:
        return "A missão apresentou tendência de PIORA."
    elif riscos[-1] < riscos[0]:
        return "A missão apresentou tendência de MELHORA."
    else:
        return "A missão permaneceu ESTÁVEL em relação ao início."

# FUNÇÃO: IDENTIFICAR ÁREA MAIS AFETADA

def identificar_area_mais_afetada(pontos_por_area):
    max_pontos = max(pontos_por_area)
    indice     = pontos_por_area.index(max_pontos)
    return indice, areas_monitoradas[indice], max_pontos

# FUNÇÃO: GERAR RELATÓRIO FINAL

def gerar_relatorio_final(riscos, pontos_por_area, medias):
    #Exibe o relatório consolidado da missão no terminal
    ciclo_critico   = riscos.index(max(riscos)) + 1
    risco_medio     = sum(riscos) / len(riscos)
    qtd_criticos    = sum(1 for r in riscos if r >= 6)
    tendencia       = analisar_tendencia(riscos)
    idx_area, nome_area, _ = identificar_area_mais_afetada(pontos_por_area)

    # Classificação final: baseada no risco médio
    classificacao_final = classificar_ciclo(round(risco_medio))

    print("=" * 60)
    print("RELATÓRIO FINAL DA MISSÃO")
    print("=" * 60)
    print(f"Missão                    : {NOME_MISSAO}")
    print(f"Equipe                    : {NOME_EQUIPE}")
    print(f"Qtd. de ciclos analisados : {len(dados_missao)}")
    print("-" * 60)
    print(f"Média de temperatura      : {medias[0]:.2f} °C")
    print(f"Média de comunicação      : {medias[1]:.2f}%")
    print(f"Média de bateria          : {medias[2]:.2f}%")
    print(f"Média de oxigênio         : {medias[3]:.2f}%")
    print(f"Média de estabilidade     : {medias[4]:.2f}%")
    print("-" * 60)
    print(f"Ciclo mais crítico        : Ciclo {ciclo_critico}")
    print(f"Maior pontuação de risco  : {max(riscos)}")
    print(f"Risco médio da missão     : {risco_medio:.2f}")
    print(f"Ciclos críticos           : {qtd_criticos}")
    print("-" * 60)
    print("Tendência da missão:")
    print(f"  {tendencia}")
    print("-" * 60)
    print("Pontuação acumulada por área:")
    for i, area in enumerate(areas_monitoradas):
        print(f"  {area}: {pontos_por_area[i]} pontos")
    print(f"\nÁrea mais afetada: {nome_area}")
    print("-" * 60)
    print(f"Classificação final da missão: {classificacao_final}")
    print("-" * 60)

    # Conclusão automática
    if classificacao_final == "MISSÃO CRÍTICA":
        conclusao = ("A missão encontra-se em estado crítico. "
                     "Ações emergenciais devem ser tomadas imediatamente "
                     "para garantir a segurança da operação.")
    elif classificacao_final == "MISSÃO EM ATENÇÃO":
        conclusao = ("A missão apresentou instabilidade relevante durante a operação. "
                     "Apesar da tentativa de recuperação no último ciclo, ainda existem "
                     "sistemas em atenção e a equipe deve manter o plano de contingência ativo.")
    else:
        conclusao = ("A missão transcorreu dentro dos parâmetros aceitáveis. "
                     "Manter monitoramento contínuo e registrar os dados para análise posterior.")

    print("Conclusão:")
    print(f"  {conclusao}")
    print("=" * 60)

# PROGRAMAÇÃO PRINCIPAL

def main():
    print("=" * 60)
    print("MISSION CONTROL AI")
    print("=" * 60)
    print(f"Missão : {NOME_MISSAO}")
    print(f"Equipe : {NOME_EQUIPE}")
    print(f"Quantidade de ciclos analisados: {len(dados_missao)}")
    print("=" * 60)

    riscos         = []          # pontuação de risco por ciclo
    pontos_por_area = [0] * 5   # acumulado de risco por área

    # Acumuladores para médias
    somas = [0.0] * 5

    for numero_ciclo, ciclo in enumerate(dados_missao, start=1):
        temperatura, comunicacao, bateria, oxigenio, estabilidade = ciclo

        # Analisar cada área
        res_temp = analisar_temperatura(temperatura)
        res_com  = analisar_comunicacao(comunicacao)
        res_bat  = analisar_bateria(bateria)
        res_oxi  = analisar_oxigenio(oxigenio)
        res_est  = analisar_estabilidade(estabilidade)

        resultados = [res_temp, res_com, res_bat, res_oxi, res_est]

        # Pontuação do ciclo
        pontuacao_ciclo = sum(pts for _, pts, _ in resultados)
        riscos.append(pontuacao_ciclo)

        # Acumular por área
        for i, (_, pts, _) in enumerate(resultados):
            pontos_por_area[i] += pts

        # Acumular para médias
        for i, val in enumerate(ciclo):
            somas[i] += val

        # Classificação e recomendação
        classificacao = classificar_ciclo(pontuacao_ciclo)
        recomendacao  = gerar_recomendacao(resultados)

        # Exibir ciclo
        print(f"\nCICLO {numero_ciclo}")
        print("-" * 60)
        print(f"Temperatura  : {temperatura} °C  | {res_temp[0]:8} | {res_temp[2]}")
        print(f"Comunicação  : {comunicacao}%     | {res_com[0]:8} | {res_com[2]}")
        print(f"Bateria      : {bateria}%         | {res_bat[0]:8} | {res_bat[2]}")
        print(f"Oxigênio     : {oxigenio}%        | {res_oxi[0]:8} | {res_oxi[2]}")
        print(f"Estabilidade : {estabilidade}%    | {res_est[0]:8} | {res_est[2]}")
        print(f"Pontuação de risco do ciclo: {pontuacao_ciclo}")
        print(f"Classificação do ciclo     : {classificacao}")
        print(f"Recomendação: {recomendacao}")

    # Calcular médias
    medias = [somas[i] / len(dados_missao) for i in range(5)]

    # Relatório final
    print()
    gerar_relatorio_final(riscos, pontos_por_area, medias)


if __name__ == "__main__":
    main()
