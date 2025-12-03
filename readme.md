# Estudo sobre Edulcorantes / Doces Sintéticos (Bioisosterismo Computacional)

**Uma investigação sobre os mecanismos moleculares da Sucralose.**

## Resumo

A sucralose é um edulcorante de alta intensidade (muito utilizado) derivado da sacarose, sendo aproximadamente **600x mais doce**, porém isenta de calorias. Este projeto utiliza Química Computacional (DFT e Modelagem Molecular) para investigar como a substituição estratégica de grupos funcionais (Hidroxila $\to$ Cloro) altera o reconhecimento molecular e bloqueia a metabolização desta substância pelo organismo humano.

## Fundamentação Teórica

Descoberta em 1976, a sucralose (triclorosacarose) consolidou-se como líder global entre adoçantes pela sua estabilidade de pH e sabor. Quimicamente definida como **4,1',6'-tricloro-4,1',6'-trideoxigalactosacarose** (ou 1',6'-Dicloro-1',6'-dideoxi-β-D-fructofuranosil-4-cloro-4-deoxi-α-D-galactopiranosídeo), sua síntese envolve a cloração seletiva de três posições específicas da sacarose, acompanhada de uma inversão de configuração no Carbono-4 [4].

Este processo exemplifica o **Bioisosterismo Não-Clássico**, uma estratégia crucial no design de fármacos e aditivos alimentares.

- **Hipótese:** O átomo de Cloro atua como um bioisóstero da Hidroxila. Ele mimetiza o volume estérico necessário para ativar os receptores de sabor doce (T1R2/T1R3), mas altera drasticamente a densidade eletrônica local, impedindo o reconhecimento pelas enzimas digestivas (glicosidases).

    
## Metodologia (Workflow)

O estudo seguiu o seguinte pipeline para a modelagem molecular:

1. **RDKit**: Para a geração de conformeros 3D iniciais via MMFF94, a partir dos SMILES do *PubChem*.
    
2. **Psi4 1.4**: Cálculos de Energia e Função de Onda utilizando Teoria do Funcional da Densidade com uma base simples (**DFT B3LYP/3-21G**) para um resultado rápido, conforme o propósito do estudo de uma simples aproximação visual.
    
3. **Análise de Superfície**: Mapeamento do Potencial Eletrostático (MEP) sobre a densidade eletrônica (Isovalue 0.002 a.u.).
    
4. **Visualização:** Renderização volumétrica com _Ambient Occlusion_ no **UCSF ChimeraX 1.10.1**.


## Resultados e Discussão

### Energias Calculadas (Single Point DFT)

- **Sacarose ($C_{12}H_{22}O_{11}$):** -1215.9255 Ha

![sucrose](https://raw.githubusercontent.com/meanmathics/adocante/refs/heads/main/img/Sucrose.png)
_(Figura 1: Estrutura 2D da Sacarose - Fonte: PubChem)._
    
- **Sucralose ($C_{12}H_{19}Cl_3O_8$):** -2324.6207 Ha

![sacralose](https://raw.githubusercontent.com/meanmathics/adocante/refs/heads/main/img/Sucralose.png)
_(Figura 2: Estrutura 2D da Sucralose. Note os átomos de Cloro nas posições 1', 4 e 6' - Fonte: PubChem)._

(A grande diferença energética reflete a contribuição dos elétrons dos átomos pesados de Cloro).
    
### Análise Visual

![comparaçao](https://raw.githubusercontent.com/meanmathics/adocante/refs/heads/main/img/compara%C3%A7ao.png)
_(Fig 3: Comparação de Potencial Eletrostático (MEP) renderizada no ChimeraX. Esquerda: Sacarose; Direita: Sucralose. Superfícies coloridas por potencial: Azul = Positivo/Doador H; Vermelho = Negativo/Aceitador H)._
A análise sugere dois fatores determinantes para as propriedades da Sucralose:
1.  **Inversão de Configuração (C4):** A inversão transforma a subunidade de glicose em um análogo de **galactose**. Enzimas humanas são estereoespecíficas; a mudança na orientação espacial impede o "encaixe" correto para a hidrólise.
2.  **Lipofilicidade e Eletronegatividade:** O Cloro é um halogênio eletronegativo, mas não forma pontes de hidrogênio fortes como a hidroxila. A visualização mostra que o Cloro "apaga" a carga positiva (azul) necessária para a catálise enzimática. A molécula consegue ativar o receptor de sabor (que é mais tolerante e focado em forma/volume), mas "escorrega" pelas enzimas digestivas, resultando em **zero calorias** metabolizáveis.

## Conclusão

A transformação da sacarose em sucralose é um caso clássico de engenharia molecular. A modificação não cria apenas um adoçante mais potente; ela gera uma nova entidade química onde a **forma** (mantida) engana o paladar, mas a **distribuição eletrônica** (alterada pelo Cloro) engana o metabolismo. Este estudo valida visualmente o conceito de bioisosterismo aplicado à indústria alimentícia.

## Referências Bibliográficas

1.  **PubChem** - Sucralose (CID 56843336). Disponível em: https://pubchem.ncbi.nlm.nih.gov/. Acessado em 12/2025.
2.  **PubChem** - Sucrose (CID 5988). Disponível em: https://pubchem.ncbi.nlm.nih.gov/. Acessado em 12/2025.
3.  **FDA** - *Sweetness Intensity of Sweeteners Compared to Table Sugar*. Disponível em: https://www.fda.gov/. Acessado em 12/2025.
4.  **Aguayo-Guerrero, J. A., et al.** (2024). Sucralose: From Sweet Success to Metabolic Controversies. *Life*, 14(3), 323.
5.  **Meng, E. C., et al.** (2023). UCSF ChimeraX: Tools for structure building and analysis. *Protein Science*, 32(11), e4792.
6.  **Smith, D. G. A., et al.** (2020). Psi4 1.4: Open-Source Software for High-Throughput Quantum Chemistry. *J. Chem. Phys*.
