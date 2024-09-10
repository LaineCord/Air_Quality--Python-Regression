# 1. Informações do conjunto de dados  

Contém as respostas de um dispositivo multissensor de gás implantado em campo em uma cidade italiana. As médias de respostas horárias são registradas junto com referências de concentrações de gás de um analisador certificado.

## 1.1 Informações adicionais

O conjunto de dados contém 9358 instâncias de respostas médias horárias de uma matriz de 5 sensores químicos de óxido de metal incorporados em um dispositivo multissensor químico de qualidade do ar. O dispositivo estava localizado no campo em uma área significativamente poluída, no nível da estrada, dentro de uma cidade italiana. Os dados foram registrados de março de 2004 a fevereiro de 2005 (um ano), representando as gravações mais longas disponíveis gratuitamente de respostas de dispositivos de sensores químicos de qualidade do ar implantados em campo. Concentrações médias horárias do Ground Truth para CO, hidrocarbonetos não metânicos, benzeno, óxidos de nitrogênio totais (NOx) e dióxido de nitrogênio (NO2) e foram fornecidas por um analisador certificado de referência co-localizado. Evidências de sensibilidades cruzadas, bem como desvios de conceito e sensor estão presentes, conforme descrito em De Vito et al., Sens. And Act. B, Vol. 129,2,2008 (citação necessária), eventualmente afetando as capacidades de estimativa de concentração dos sensores. Valores ausentes são marcados com valor -200.

# 2.Bibliotecas
Foram utilizadas bibliotecas do Pandas, Numpy, Seaborn, Matplotlib e Lightgbm.

# 3. Variáveis do Dataset

![image](https://github.com/user-attachments/assets/a4384f8a-11e0-4a9c-8293-ed07586e7600)

- CO = O monóxido de carbono (CO) é um gás levemente inflamável, inodoro e muito perigoso devido à sua grande toxicidade. É produzido pela queima em condições de pouco oxigênio (combustão incompleta) e/ou alta temperatura de carvão ou outros materiais ricos em carbono, como derivados de petróleo, por exemplo, pelos motores dos veículos.

- NMHC = Os hidrocarbonetos não metânicos (HCNM) ou hidrocarbonetos não metano são compostos muito reativos que interferem no ciclo global do carbono, na concentração desse elemento na atmosfera e na capacidade de oxidação dela.Esses compostos são produzidos principalmente por meio do metabolismo secundário das folhas.A emissão dos 8% restantes de HCNM é proveniente de atividades humanas, como da produção de energia, dos automóveis e das indústrias, pois esses gases são produzidos na combustão incompleta dos combustíveis, como a gasolina, o gás natural e o GLP (Gás Liquefeito de Petróleo).

- C6H6 = O benzeno ou C6H6 é um líquido incolor, altamente inflamável e com odor adocicado. É utilizado na produção de plásticos, fibras sintéticas, borracha, pesticidas e outros produtos químicos. É um conhecido agente cancerígeno e pode causar problemas de saúde.

- NO2 = O dióxido de nitrogênio (NO2) é um dos gases altamente reativos conhecidos como óxidos de nitrogênio (NOx). As principais fontes de emissões antropogênicas de NO2 são os processos de combustão. Respirar ar com alta concentração de NO2 pode irritar as vias aéreas no sistema respiratório humano.

- O3 = Poluição por ozônio é um tipo de poluição causado a partir de reações químicas entre raios solares, gases presentes na atmosfera e compostos liberados por veículos, processos industriais e instalações como usinas de energia e aterros sanitários. Apesar desse gás ser extremamente necessário para bloquear parte da radiação solar que chega à superfície terrestre, o ozônio formado na troposfera a partir de reações químicas com outros poluentes causa diversos danos à saúde humana e ao meio ambiente.

- T = A temperatura ambiente é um parâmetro básico que influencia a dispersão de poluentes e a formação de ozônio troposférico. Altas temperaturas podem aumentar as reações químicas que geram ozônio.

- RH = É a relação entre a umidade absoluta do ar e o seu ponto de saturação (é o limite pelo qual a atmosfera pode aumentar a quantidade de vapor d’água. Quando este é atingido, dizemos que o ar está saturado; quanto maior a temperatura, maior a quantidade de vapor de água que o ar poderá conter, e, consequentemente, maior será o ponto de saturação). A umidade relativa afeta a formação de nevoeiros e a dispersão de poluentes. Alta umidade pode reduzir a dispersão de certos poluentes, exacerbando a poluição local.

- AH = É a quantidade de vapor de água existente na atmosfera num dado momento. A AH influencia a formação de nevoeiros, chuvas e a dispersão de poluentes. Em climas úmidos, pode haver maior retenção de certos poluentes no ar.

Em suma, a variação para cima ou para baixo de alguns desses compostos indicam a interferência de atividades humanas industriais que afetam diretamente na saúde pública.

# 4. Objetivo do Estudo: Desenvolver um modelo preditivo que seja capaz de prever a qualidade do ar com base em dados meterológicos e de poluição.

# 5. EDA - Análise Exploratória dos Dados
## 5.1 Linearidade da coleta dos dados:
![image](https://github.com/user-attachments/assets/8133137a-116f-463e-be45-715ed86cf0a6)

A coleta de dados parece seguir um padrão em quantidade para grande parte dos meses coletados, com exceção dos meses 03/2004 e 04/2005.

## 5.2 Correlação das variáveis do Dataset:

![image](https://github.com/user-attachments/assets/ae3acf51-38bf-43a7-95cb-f499d1c5aee7)

Há uma boa correlação para as variáveis analisadas de modo geral, principalmente para as variáveis  >0.90 como temperatura com umidade relativa e umidade absoluta.
Temperatura, Umidade relativa e umidade absoluta com com CgH6(GT).

Também há uma forte correlação entre as variáveis PT08.S(03) e PT08.S2(NMHC) e PT08.S2(NMHC) com PT08.S1(CO).

## 5.3 Distribuição das variáveis ao longo do dia:

![image](https://github.com/user-attachments/assets/b3053317-81cb-497e-93f8-b05c78d3afd8)
![image](https://github.com/user-attachments/assets/26e154fd-c94a-4222-8b6c-b3467b6a9be6)
![image](https://github.com/user-attachments/assets/a42f0518-e8fc-40cb-ada7-b8a26a7bdac3)
![image](https://github.com/user-attachments/assets/68e43d9b-dc96-4555-9877-15a608412bbc)
![image](https://github.com/user-attachments/assets/ae498206-0149-45c5-becd-db90f178141a)
![image](https://github.com/user-attachments/assets/35d5eb79-7659-4f0e-adb9-b7655db4b686)
![image](https://github.com/user-attachments/assets/2fb812a9-8f63-4ca0-943e-0f9c8c52dc05)
![image](https://github.com/user-attachments/assets/fc7da9b2-b152-4f4f-b13c-e160011e72c1)
![image](https://github.com/user-attachments/assets/319cc526-a9b4-4d68-a420-a2e0b9659949)
![image](https://github.com/user-attachments/assets/e54c4783-361d-4112-a8fa-d34f72b8d8dd)
![image](https://github.com/user-attachments/assets/d42c3d4b-2ffe-4ec2-9236-b0b2122c702e)
![image](https://github.com/user-attachments/assets/fb58f065-40a9-4288-89f3-c529aaf729e5)


# 6. Modelos utilizados
Para este estudo foram utlizados os modelos:
- lgb.LGBMRegressor(),
- LinearRegression(),
- linear_model.Lasso(alpha=0.1),
- GradientBoostingRegressor(),
- KNeighborsRegressor(),
- MLPRegressor(),
- DecisionTreeRegressor()

# 7. Resultados 
![image](https://github.com/user-attachments/assets/4acee017-f933-4cdc-a9e0-eaa4e683a900)

![image](https://github.com/user-attachments/assets/5d80b5d4-f775-40dd-a0df-10e6fcab5a09)


O modelo que melhor se comportou nos testes realizados foi o LGBMRegressor, por conseguinte do DecisionTreeRegressor.


