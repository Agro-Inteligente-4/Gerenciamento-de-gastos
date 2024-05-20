# Gerenciamento-de-gastos

## Automação dos Cálculos de Custo de Produção Agrícola de Açúcar e Álcool no Brasil

### Equações: 
```{python}
def calculate_COPterra(ATRpadrao, P, ATR, HAproprio):
    COPterra = ATRpadrao * P * ATR * HAproprio
    return COPterra

def calculate_COPcapital(CI, r):
    COPcapital = CI * r
    return COPcapital

def calculate_CT(C_OT, C_OP_terra, C_OP_capital):
    CT = C_OT + C_OP_terra + C_OP_capital
    return CT

def calcular_cot(cof, Di):
    cot = cof + Di
    return cot
```

```{python}
def calculate_depreciation(Vi, Vr, Vu, G):
    Di = (Vi - Vr) / Vu * G
    return Di
```

```{python}
def calculate_OPERATION_cost(CMAQ, PHM, CMOB, PMOB, CINS, PINS, HA):
    OPER = (CMAQ * PHM) + (CMOB * PMOB) + (CINS * PINS) * HA
    return OPER

# Equação 2
def calculate_ADMIN_cost(SAL, MAT, SEG, MAN, CONT, ALIM, SERV, OUTR):
    ADM = SAL + MAT + SEG + MAN + CONT + ALIM + SERV + OUTR
    return ADM

# Equação 3
def calculate_TOTAL_LEASE_cost(CATRPADRÃO, PATR, PARREND, HA):
    RENDIMENTO = CATRPADRÃO * PATR
    CUSTOARREND = RENDIMENTO * PARREND * HA
    return CUSTOARREND

# Equação 4
def calculate_EFFECTIVE_OPERATIONAL_COST(OPER, ADM, CUSTOARREND):
    COE = OPER + ADM + CUSTOARREND
    return COE
```

### Detalhamento das variáveis:

##### Custo Operacional Efetivo (COE)

1. **OPERi (Custo da Operação i)**:
   - Representa o custo associado à execução de uma operação específica, incluindo custos diretos e indiretos como combustível, manutenção de equipamentos, depreciação, entre outros. Calculado com base em custos reais ou estimados.

2. **cMAQ (Coeficiente de Utilização da Máquina e/ou Equipamento na Operação i)**:
   - Indica a eficiência ou a proporção de tempo que a máquina ou equipamento é utilizado na operação, variando de 0 a 1.

3. **PHM (Preço da Máquina e/ou Equipamento)**:
   - Custo associado ao uso da máquina ou equipamento por unidade de tempo, distância ou quantidade de trabalho realizado.

4. **cMOB (Coeficiente de Utilização da Mão-de-obra na Operação i)**:
   - Reflete a eficiência ou a proporção do tempo em que a mão-de-obra está ativamente envolvida na operação.

5. **PMOB (Preço da Mão-de-obra)**:
   - Custo associado à utilização da mão-de-obra por dia de trabalho, incluindo salários, benefícios e outros custos relacionados.

6. **cINS (Coeficiente de Utilização do Insumo na Operação i)**:
   - Indica a quantidade de insumo utilizado em relação à operação.

7. **PINS (Preço do Insumo)**:
   - Custo do insumo por unidade de dose, podendo ser medido em reais por tonelada, quilo, litro, etc.

8. **HA (Número de Hectares)**:
   - Representa a extensão de terra em que a operação foi realizada.

##### Custos Administrativos (ADM)

1. **ADM (Custos Administrativos)**:
   - Custo geral associado à administração da fazenda, incluindo salários da equipe administrativa, aluguel de escritórios, despesas com tecnologia da informação, entre outros.

2. **SAL (Gasto com Salários)**:
   - Custos associados aos salários dos funcionários, incluindo encargos sociais e benefícios.

3. **MAT (Gastos com Materiais de Escritório)**:
   - Custos associados à compra de materiais de escritório.

4. **SEG (Gasto com Seguros de Benfeitorias Agrícolas)**:
   - Custos associados aos prêmios de seguro para cobrir benfeitorias agrícolas.

5. **MAN (Gasto com Manutenção de Benfeitorias Agrícolas)**:
   - Custos de manutenção para garantir que as benfeitorias agrícolas estejam em boas condições.

6. **CONT (Gasto com Contas em Geral)**:
   - Despesas diversas relacionadas à administração da fazenda, como contas de água, eletricidade, internet, telefone, etc.

7. **ALIM (Gasto com Alimentação dos Funcionários)**:
   - Custos associados à alimentação dos funcionários.

8. **SERV (Gasto com Serviços Subsidiados para os Funcionários)**:
   - Custos de serviços subsidiados oferecidos aos funcionários, como transporte e creche.

9. **OUTR (Gasto com Outros Custos Administrativos Relevantes)**:
   - Outros custos administrativos que não foram especificados nas categorias anteriores.

##### Gasto Total com Arrendamentos (ARREND)

1. **ARREND (Gasto Total com Arrendamentos)**:
   - Representa o custo total associado ao arrendamento de terras.

2. **cATRPADRÃO (Coeficiente Padrão Fixado na Região)**:
   - Mede a quantidade de ATR (Açúcar Total Recuperável) em quilogramas por tonelada de cana, fixado na região em análise.

3. **PATR (Preço do Quilograma de ATR Praticado na Região)**:
   - Preço do quilograma de ATR na região em análise.

4. **PARREND (Preço do Contrato de Arrendamento)**:
   - Preço do contrato de arrendamento praticado na região, medido em toneladas de cana por hectare.

5. **HA (Número de Hectares Arrendados)**:
   - Número de hectares de terra arrendados.

##### Custo Operacional Total (COT)

1. **COE (Custo Operacional Efetivo)**:
   - Soma de todos os custos operacionais efetivos.

2. **Di (Depreciação do Item i)**:
   - Depreciação medida em reais por tonelada de cana.

##### Custo Total (CT)

1. **COPterra (Custo de Oportunidade da Terra Própria)**:
   - Custo associado ao uso da terra própria, considerando o potencial de renda se a terra fosse usada para outras finalidades.

2. **ATRpadrão (Quantidade de ATR Fixa nos Contratos de Arrendamento)**:
   - Quantidade fixa de ATR estipulada nos contratos de arrendamento na região analisada.

3. **PATR (Preço do ATR Praticado)**:
   - Preço do quilograma de ATR praticado.

4. **Parrend (Preço do Arrendamento Praticado)**:
   - Preço do arrendamento praticado, medido em toneladas de cana por hectare.

5. **HApróprio (Número de Hectares Cultiváveis Próprios)**:
   - Número de hectares de terra própria que o agricultor possui e pode cultivar.

6. **i (Investimentos de Capital)**:
   - Representa o tipo de investimento de capital, como fundação da lavoura, equipamentos de irrigação/fertirrigação, máquinas, implementos ou benfeitorias.

7. **COPcapital (Custo de Oportunidade do Capital Investido)**:
   - Custo de oportunidade do capital investido, medido em reais.

8. **CI (Capital Investido em i)**:
   - Montante de capital investido em i, medido em reais.

9. **r (Taxa de Juros)**:
   - Taxa de retorno ou custo do capital investido.

Em resumo, esses cálculos envolvem uma combinação de dados reais, estimativas e suposições informadas para determinar os custos associados à produção agrícola de açúcar e álcool. Utilizando essas variáveis, é possível automatizar e otimizar o processo de cálculo de custos, melhorando a eficiência e a lucratividade dos produtores.
