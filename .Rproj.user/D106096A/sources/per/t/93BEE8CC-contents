
# Instalação e Carregamento dos Pacotes -----------------------------------
# install.packages("dplyr")
# install.packages("readxl")
# install.packages("ggplot2")

library(dplyr)
library(readxl)
library(ggplot2)

# Importação e Conhecimento dos Dados -------------------------------------
vendas_df <- read_excel('Vendas.xlsx')

head(vendas_df)
str(vendas_df)
summary(vendas_df)

# Manipulação dos Dados  --------------------------------------------------

# Calcular faturamento
faturamento <-  sum(vendas_df$Valor_Final)
faturamento

# Faturamento por Loja 
faturamento_loja <- vendas_df %>% 
  group_by(ID_Loja) %>% 
  summarise(Faturamento_total = sum(Valor_Final))

# Calcular faturamento por produto
faturamento_produto <- vendas_df %>%
  group_by(ID_Loja, Produto) %>%
  summarise(Faturamento_produto_total = sum(Valor_Final))

# Visualização dos Dados --------------------------------------------------
ggplot(data = faturamento_loja, mapping = aes(x = ID_Loja, y = Faturamento_total)) + 
  geom_col() + 
  theme_classic() +
  labs(
    title = 'Faturamento por Loja',
    x = NULL,
    y = 'Faturamento'
    )

ggplot(data = faturamento_produto, mapping = aes(x = ID_Loja, y = Faturamento_produto_total, fill = Produto)) + 
  geom_col(position = 'dodge') +
  theme_minimal() + 
  labs(
    title = 'Faturamento de cada produto por loja',
    x = NULL,
    y = 'Faturamento'
    )
