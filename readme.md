# Estudo sobre Doces Sintéticos (Bioisosterismo Computacional)

**Uma investigação sobre os mecanismos moleculares da Sucralose.**

## Resumo

A sucralose é um adoçante artificial (muito utilizado) derivado da sacarose que é aproximadamente **600x mais doce**, porém possui **zero calorias**. Este projeto utiliza Química Computacional (DFT) para investigar como uma simples substituição atômica (Hidroxila $\to$ Cloro) altera fundamentalmente o reconhecimento molecular e o metabolismo desta substância no corpo humano.

## Fundamentação Teórica

A premissa central apresentada — de que "A Sucralose é feita trocando grupos Hidroxila (-OH) da Sacarose por Cloro (-Cl)" — constitui a base fundamental para a compreensão não apenas das propriedades organolépticas deste adoçante, mas também de todo o seu perfil toxicológico, metabólico e ambiental. Esta modificação estrutural, aparentemente simples, onde três átomos de cloro substituem três grupos hidroxila na molécula de açúcar natural, transforma um nutriente calórico e biodegradável numa molécula organoclorada sintética de elevada estabilidade e potência adoçante extraordinária.   
Descoberta em 1976 através de uma colaboração entre a Tate & Lyle e o Queen Elizabeth College, a sucralose (triglicerosacarose) emergiu como o edulcorante de alta intensidade dominante globalmente, celebrado pela sua estabilidade de pH e perfil de sabor superior em comparação com antecessores como a sacarina e o aspartame. A sua estrutura química, 1,6-dicloro-1,6-dideoxi-β-D-fructofuranosil-4-cloro-4-deoxi-α-D-galactopiranosídeo, confere-lhe uma doçura estimada entre 400 a 700 vezes superior à da sacarose, dependendo da matriz em que é dissolvida [4].
A sucralose é sintetizada pela substituição seletiva de três grupos hidroxila (-OH) por átomos de Cloro (-Cl), acompanhada de uma inversão de configuração no Carbono-4. Um processo muito utilizado no design de novas moléculas, chamado **Bioisosterismo**.
- **Hipótese:** O Cloro atua como um bioisóstero não-clássico. Ele mimetiza o volume estérico da hidroxila (mantendo o sabor doce), mas altera drasticamente a distribuição eletrônica (impedindo a digestão por ser sintético).

    
## Metodologia (Workflow)

O estudo seguiu o seguinte pipeline para a modelagem molecular:

1. **RDKit**: Para a geração de conformeros 3D iniciais via MMFF94, a partir dos dados do **PubChem**.
    
2. **Psi4 1.4**: Cálculos de Energia e Função de Onda utilizando Teoria do Funcional da Densidade com uma base simples (**DFT B3LYP/3-21G**) para um resultado rápido, conforme o propósito do estudo de uma aproximação visual.
    
3. **Análise de Superfície**: Mapeamento do Potencial Eletrostático (MEP) sobre a densidade eletrônica (Isovalue 0.002 a.u.).
    
4. **Visualização:** Renderização volumétrica com _Ambient Occlusion_ no **UCSF ChimeraX 1.10.1**.


## Resultados e Discussão

### Energias Calculadas (Single Point DFT)

- **Sacarose ($C_{12}H_{22}O_{11}$):** -1215.9255 Ha

![sucrose](https://raw.githubusercontent.com/meanmathics/adocante/refs/heads/main/img/Sucrose.png)
_(Figura 1: Sacarose ou Sucrose PubChem)._
    
- **Sucralose ($C_{12}H_{19}Cl_3O_8$):** -2324.6207 Ha

![sacralose](https://raw.githubusercontent.com/meanmathics/adocante/refs/heads/main/img/Sucralose.png)
_(Figura 2: Sacralose PubChem)._

(A grande diferença energética reflete a contribuição dos elétrons dos átomos pesados de Cloro).
    
### Análise Visual

![comparaçao](https://raw.githubusercontent.com/meanmathics/adocante/refs/heads/main/img/compara%C3%A7ao.png)
_(Fig 1: Comparação de Potencial Eletrostático (MEP) entre Sacarose e Sucralose, renderizada no UCSF ChimeraX)._

As simulações revelaram diferenças críticas na superfície molecular:

- **Sacarose (Natural):** Apresenta dipolos fortes ou polaridade (regiões Azul/Vermelho intensas), facilitando a solvatação e o acoplamento com enzimas hidrolíticas (Invertase).
    
- **Sucralose (Sintética):** A substituição por Cloro (átomos maiores!) remove os sítios doadores de ligação de hidrogênio (regiões azuis). Isso cria uma blindagem hidrofóbica e eletrônica local que impede o ataque enzimático, resultando na não-metabolização na digestão (0 kcal).
Esta alteração é crítica por várias razões físico-químicas:
1. Inversão de Configuração: A inversão do grupo hidroxila no carbono-4 transforma a porção de glicose numa estrutura de 4-cloro-4-deoxigalactose. Esta mudança estereoquímica é fundamental porque as enzimas glicosídicas do trato digestivo humano, como a sacarase e a invertase, são altamente específicas para a conformação da sacarose. A alteração impede o reconhecimento enzimático, tornando a molécula resistente à hidrólise digestiva e, teoricamente, não calórica.   
2. Lipofilicidade e Eletronegatividade: O cloro é significativamente mais lipofílico e eletronegativo do que o grupo hidroxila. A substituição aumenta a hidrofobicidade da molécula em regiões chave. Enquanto os grupos hidroxila funcionam como doadores e aceitadores de ligações de hidrogênio, os átomos de cloro atuam principalmente como sítios hidrofóbicos densos em elétrons. Esta alteração nas propriedades eletrônicas e estéricas é o que permite à sucralose interagir com o receptor de sabor doce com uma afinidade centenas de vezes superior à do seu análogo natural.

## Conclusão

A afirmação de que a sucralose é derivada da sacarose pela troca de grupos hidroxila por cloro é a chave para entender tanto o seu sucesso comercial quanto os seus riscos biológicos. Essa modificação não cria apenas um adoçante; cria uma molécula nova com propriedades fundamentalmente distintas da sua precursora natural, especialmente as químicas, em relação a versão natural (açucar) como o fato de ser centenas de vezes *mais doce*.

## Referências Bibliográficas

1. PubChem - Sucralose. Disponível em: https://pubchem.ncbi.nlm.nih.gov/compound/Sucralose. Acessado em 12/2025.
2. PubChem - Sacarose. Disponível em: https://pubchem.ncbi.nlm.nih.gov/compound/5988. Acessado em 12/2025
3. FDA - Sweetness Intensity of Sweeteners Compared to Table Sugar. Disponivel em: https://www.fda.gov/media/168345/download. Acessado em 12/2025.
4. Aguayo-Guerrero JA, Méndez-García LA, Solleiro-Villavicencio H, Viurcos-Sanabria R, Escobedo G. Sucralose: From Sweet Success to Metabolic Controversies-Unraveling the Global Health Implications of a Pervasive Non-Caloric Artificial Sweetener. Life (Basel). 2024 Feb 29;14(3):323. doi: 10.3390/life14030323. PMID: 38541649; PMCID: PMC10971371.
5. UCSF ChimeraX: Tools for structure building and analysis. Meng EC, Goddard TD, Pettersen EF, Couch GS, Pearson ZJ, Morris JH, Ferrin TE. Protein Sci. 2023 Nov;32(11):e4792.
6. Smith, D. G. A., et al. (2020). Psi4 1.4: Open-Source Software. J. Chem. Phys.




