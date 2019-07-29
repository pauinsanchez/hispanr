#' Choropleth map for current Spanish provinces
#'
#' This function creates a choropleth map for Spanish provinces
#' @param data A dataframe containing the variable assigned to each province, using base file
#' @param a A vector specifying the breakpoints of the desired choropleth intervals
#' @param color A ColorBrewer sequential palette
#' @keywords maps choropleth spain
#' @import dplyr sf dplyr RColorBrewer ggplot2
#' @export
#' @examples
#' provmap(data, c(0, 10, 20, 30, 40), "Reds")

provmap <- function(data, a, color){
  # join the map with the data
  mapdata <<- inner_join(map, data)
  # obtain a vector with the intervals
  b <- paste(a[-length(a)], a[-1], sep = " - ")
  # assign intervals to each observation
  mapdata$sum <- cut(mapdata$data, breaks = a, labels = b, include.lowest = TRUE)
  # obtain the color palette
  colorsP <- brewer.pal(length(b), color)
  # create the map
  map <- ggplot(mapdata) +
    geom_sf(aes(fill = mapdata[[9]]), color = "black") +
    theme(axis.text.x = element_blank(),
          axis.text.y = element_blank(),
          axis.ticks = element_blank(),
          rect = element_blank(),
          legend.position = c(0.15, 0.6),
          legend.text = element_text(color = "black", size = 14),
          legend.title = element_text(size = 14, face = "bold"),
          legend.key.size = unit(1, "cm"),
          legend.key.width = unit(1,"cm")) +
    scale_fill_manual(name = "",
                      values = setNames(colorsP, b),
                      breaks = rev(b),
                      labels = rev(b),
                      na.value = "black")
  # plot the map
  plot(map)
}
