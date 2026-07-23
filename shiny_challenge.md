## Assignment 2 🌐 

Can you write an R script to create a shiny app with the functionality shown in the video below utilizing the [county_data.gpkg](https://github.com/NSF-ALL-SPICE-Alliance/DS421-Carto-Design/blob/main/data/county_data.gpkg) and the following packages. Please name this shiny_app_language.qmd and push to your github repository

```r
library(shiny)
library(mapview)
library(here)
library(sf)
library(tidyverse)
library leaflet
```


### Use this example from class to help you from the fire data

```r
ui <- fluidPage(
  titlePanel("Fire Predictions"),
  sidebarLayout(
    sidebarPanel(
      selectInput(
        "var",
        "Choose fire confidence",
        choices = unique(sf_fire_csv_data$confidence)
      )
    ),
    mainPanel(
      leafletOutput("map", height = "700px")
    )
  )
)

server <- function(input, output, session) {
  output$map <- renderLeaflet({
    filtered_data <- sf_fire_csv_data[sf_fire_csv_data$confidence == input$var, ]
    
    mapview(
      filtered_data,
      zcol = "confidence",   # column name, fixed
      layer.name = "Confidence"
    )@map
  })
}

shinyApp(ui, server)
```

### Tips 
- This is a .gpkg file (new to us) but you can read it in with st_read()
- The dataframe should have everything you need, no need for new calculations/columns




https://github.com/user-attachments/assets/5f5327e4-7a42-4439-8350-0fc6c0be064f





