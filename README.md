# Unique species in the dataset for visulaizsation
unique_species <- unique(stats_species_data$stand_spp)

# Loop through each species
for(species in unique_species) {
  # Filter data for the current species
  species_data <- filter(stats_species_data, stand_spp == species)
  
  # Generate the plot for the current species
  p <- ggplot(species_data, aes(x = mean_prop_d, y = depthstd, color = month)) +
    geom_line() +
    scale_x_continuous(position = "top") +
    scale_y_reverse(breaks = c(25, 50, 75, 100)) +
    labs(title = paste("Uptake Proportion (d) by Season for", species), 
         x = "Mean Proportional D", 
         y = "Depth (cm)") +
    theme_classic() +
    theme(axis.title.x.top = element_text(vjust = 0.05)) +
    scale_color_viridis(discrete = TRUE, option = "D") # Use viridis for color
  
  # Print the plot
  print(p)
