# TrabajoFinal_BigData_TiendaParis

# Configuracion espacio de trabajo#
setwd("C:/Users/samon/Desktop/universidad/2020/Segundo semestre/Big data/trabajofinal_bigdata")

#instalarndo Rvest
install.packages("rvest")
install.packages("gdata")

# importar las librerias
library(rvest)
library(gdata)

# descargar datos de la pagina paris para la investigacion de la playstation 4

paris <- read_html("https://www.paris.cl/tecnologia/consolas-videojuegos/juegos/juegos-ps4/playstation/")

listadoJuegosParis <- html_node(paris, css = "#primary")

# titulos de los productos
titulosParis <- html_nodes(listadoJuegosParis, ".ellipsis_text")
textTitulosParis <- html_text(titulosParis)

for (n in 1:length(textTitulosParis)) {
  print(textTitulosParis[n])
}


# precios de los productos
preciosParis <- html_nodes(listadoJuegosParis, ".price")
textPreciosParis <- html_text(preciosParis)

for (k in 1:length(textPreciosParis)) {
  print(textPreciosParis[k])
}

# [almacenando informacion 1] creacion de un dataframe

todosLosDatos <- data.frame()


for (i in 1:length(textTitulosParis)) {
  print("========== ITEM ==========")
  
  # nombre del juego:
  print(textTitulosParis[i])
  
  # precio:
  textPreciosParis <- gsub("[.]","",textPreciosParis)
  textPreciosParis <- as.character(textPreciosParis)
  print(textPreciosParis[i])
  
  # [almacenando informacion 2] creando dataframe con los detalles
  # de cada item
  
  itemParis <- data.frame(titulosParis = textTitulosParis, preciosParis = textPreciosParis)
  
  # [almacenando informacion 3] almacenando la info del producto con 
  # con los datos totales
  
  todosLosDatos <- rbind(todosLosDatos,itemParis)
  break = 40
}


# descargar datos de la pagina paris para la investigacion de la Xbox one

parisxbox <- read_html("https://www.paris.cl/tecnologia/consolas-videojuegos/juegos/xbox/")

listadoJuegosParisxbox <- html_node(parisxbox, css = "#search-result-items")

# titulos de los productos
titulosParisxbox <- html_nodes(listadoJuegosParisxbox, ".name-product-plp")
textTitulosParisxbox <- html_text(titulosParisxbox)

for (n in 1:length(textTitulosParisxbox)) {
  print(textTitulosParisxbox[n])
}


# precios de los productos
preciosParisxbox <- html_nodes(listadoJuegosParisxbox, ".default-price")
textPreciosParisxbox <- html_text(preciosParisxbox)

for (k in 1:length(textPreciosParisxbox)) {
  print(textPreciosParisxbox[k])
}

# [almacenando informacion 1] creacion de un dataframe

todosLosDatosxbox <- data.frame()


for (i in 1:length(textTitulosParisxbox)) {
  print("========== ITEM ==========")
  
  # nombre del juego:
  print(textTitulosParisxbox[i])
  
  # precio:
  textPreciosParisxbox <- gsub("[.]","",textPreciosParisxbox)
  textPreciosParisxbox <- as.character(textPreciosParisxbox)
  print(textPreciosParisxbox[i])
  
  # [almacenando informacion 2] creando dataframe con los detalles
  # de cada item
  
  itemParisxbox <- data.frame(titulosParisxbox = textTitulosParisxbox, preciosParisxbox = textPreciosParisxbox)
  
  # [almacenando informacion 3] almacenando la info del producto con 
  # con los datos totales
  
  todosLosDatosxbox <- rbind(todosLosDatosxbox,itemParisxbox)
  break = 15
}

