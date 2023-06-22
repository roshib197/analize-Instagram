# Cargar los datos de Instagram
datos_instagram <- read.csv("datos_instagram.csv")

# Crear una red de Instagram
red_instagram <- graph_from_data_frame(datos_instagram, directed = TRUE)

# Calcular las métricas de centralidad
grado <- degree(red_instagram)
intermediacion <- betweenness(red_instagram)

# Calcular la modularidad
modularidad <- modularity(red_instagram)

# Visualizar la estructura de la red
ggraph(red_instagram, layout = "fr") +
  geom_edge_link() +
  geom_node_point() +
  theme_void()

# Visualizar la relación entre los nodos
ggplot(datos_instagram, aes(x = grado, y = intermediacion)) +
  geom_point() +
  labs(x = "Grado", y = "Intermediación")
