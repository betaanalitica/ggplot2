### Exemplo de gráfico de textura 

# Pacotes: 
library(devtools) 
devtools::install_github("clauswilke/ggtextures")
library(ggtextures) 
library(ggplot2) 
library(magick)
library(tibble) 


# Dados 

df <- tibble(trt = c("Carvão", "Argila", "Papel Toalha", "Areia", "Fibra de coco", 
"Folhiço", "Vermiculita"), outcome = c(15, 35, 40, 50, 70, 80, 95), 
images = c(carvao = "carvao.jpg",
claysoil = "clay.jpg",
papel = "papel.jpg",
sandysoil = "sandy-soil.jpg",
fibracoco = "fib.jpg",
fol = "leaf-litter.jpg",
verm = "vermi.jpg"))### As imagens devem estar salvas na pasta do diretório.

# Gráfico 

ggplot(df, aes(x=reorder(trt, outcome), y=outcome, image = images)) +
geom_textured_col(img_height = unit(1, "null"), img_width = unit(4.4, "null"), width = .9) +
labs(x="Tipo de Substrato", y="Porcentagem de germinação (%)", image="Tipo de Substrato") +
theme(axis.text = element_text(colour = "#000000", size = rel(1)),
axis.title = element_text(colour = "#000000", size = rel(1.36)),
panel.background = element_rect(fill = "antiquewhite1",
colour = "cornsilk3",
size = 0.8, linetype = "solid"))
