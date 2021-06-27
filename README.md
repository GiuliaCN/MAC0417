# MAC0417
Git para a disciplina de MAC0417 - Visão e Processamento de Imagem do IME-USP oferecimento no primeiro semestre de 2021

Grupo: Giulia Nardi, Daniel Costa, Carlos Reis

---

## EP1

Base de imagens:

- Classes (objetos fotografados): desodorante, pente, faca, copo, grampeador, óculos, chave, tesoura, lapis, garfo
- São 36 fotos por objeto: 3 fundos diferentes, 4 iluminações e 3 repetições
- São de 3 à 10 objetos por classe

Padronização para aquisição de imagens:

- Fundos: branco, preto, "papelão"
- Nome da imagem: Objeto + tipo na classe(1,2,3, 4...) + fundo branco (b), preto(p) ou marrom(m) + dia(d) ou noite(n) + outside(o) ou inside(i) + versão(1,2,3).
    Ex: tesoura-2bdi1, chave-1mdo3
- Utilizar https://play.google.com/store/apps/details?id=com.vinson.shrinker no celular para ajustar o tamanho da imagem com largura de 1200px e altura proporcional.
- Foto na horizontal, com objeto inteiramente na foto e centralizado.


Pasta no drive onde se encontram as imagens: https://drive.google.com/drive/folders/1UCvz5sp8_lax59cgArrOyZSArcTVpvfI?usp=sharing


 
## EP2
 
**Objetivo:** Aumentar o conjunto de imagens por meio de transformações de frequência e de espaço. Também queremos analisar os efeitos dessas transformações nas imagens, por meio de histogramas de imagens e protótipos médios das imagens.
 
Esse trabalho foi dividido em duas partes, inicialmente foram realizadas algumas transformações nas imagens e em seguida, após gerar um grupo de imagens normalizadas, foi feita uma análise dos resultados encontrados por meio de histogramas e média das imagens.
 
### EP2.1
 
Inicialmente foi realizada a transformação das imagens coletadas no EP1 para preto e branco, gerando o dataset original Gray Dataset, que contém o resultado das transformações que foram feitas usando a função rgb2gray(imagem) da biblioteca skimage.
 
Com as imagens em preto e branco foi possível realizar as outras quatro transformações, as quais foram salvas na pasta augmentedDataset.
 
Para a soma de fundo do gradiente de cinza foi gerado um gradiente de cinza que foi multiplicado por cada imagem. Nessa função houve um pequeno problema com algumas imagens que estava com tamanho diferente das demais, para essas imagens foi necessário gerar um gradiente personalizado o que diminui a eficiência do algoritmo e deixou claro para o grupo a importância de imagens padronizadas. Mas como eram poucas imagens com esse problema o tempo para gerar as imagens não foi muito ruim.
 
Também foi realizada a transformação logarítmica a qual gerou imagens com um contraste menor entre os níveis de cinza. Para tanto foi utilizada a função exposure.adjust_log(imagem, 1) da biblioteca skimage.
 
Para a transformação exponencial, foi realizada a operação e^{pixel-1} onde foram geradas imagens mais claras, pois o range de cor ficou em [e^-1, 1] o que tornou as imagens mais claras.
 
Por fim foi realizada a transformação do filtro da média usando convolução, foi utilizada uma máscara de 3X3 o que causou um leve desfoque nas imagens. Também foi feita a cópia do originalDataset e do originalGrayDataset para o augmentedDataset, com isso o augmentedDataset ficou com seis pastas com 1080 fotos cada, totalizando 6480 imagens.
 
### EP2.2
 
Inicialmente foi realizada outra transformação usando a equalização do histograma seguida pela normalização max min das imagens, o resultado dessa transformação foi salvo na pasta normalizaDataset. Essa função ao contrário da função logarítmica aumenta o contraste das imagens.
 
Após a realização de todas as transformações obtivemos um novo dataset com mais 6480 imagens. Como todas essas imagens foi plotada o protótipo médio de cada classe em cada uma das pastas, onde foi possível ver borrões com a forma do objeto da classe. Assim como foi analisado o histograma médio das imagens e a variância de cada tom de cinza para cada classe.
 
Pelos histogramas foi possível perceber muito claramente o efeito da equalização do histograma, pois os valores dos pixels das classes do dataset normalizado apresentaram uma maior variância que os demais, onde os valores dos pixels ficaram mais concentrados.
