# Understanding `ggplot2` Graphics Grammar

`ggplot2` is a powerful and flexible R package for creating data visualizations. It is based on the Grammar of Graphics, which provides a coherent system for describing and building graphs. This chapter will serve as a self-study reference on how to manage `ggplot2` syntax.

## Providing Data

The first step in creating a plot with `ggplot2` is to provide the data. The data should be in a data frame format.

```{r}
# Load the ggplot2 package
library(ggplot2)

# Example data frame
data <- data.frame(
  x = rnorm(100),
  y = rnorm(100)
)
```

## Defining Aesthetics

Aesthetics (aes) are the visual properties of the objects in your plot, such as position, color, shape, and size. You define aesthetics using the `aes()` function.

```{r}
# Define aesthetics
ggplot(data, aes(x = x, y = y))
```

## Choosing Geoms

Geoms (geometric objects) are the actual marks we put on a plot. Examples include points, lines, bars, and histograms. You add geoms to your plot using functions like `geom_point()`, `geom_line()`, `geom_bar()`, etc.

```{r}
# Add points to the plot
ggplot(data, aes(x = x, y = y)) + geom_point()
```

## Fine-Tuning Scales

Scales control the mapping from data to aesthetics. You can adjust scales to change the appearance of your plot, such as axis labels, limits, and breaks.

```{r}
# Adjust scales
ggplot(data, aes(x = x, y = y)) + 
  geom_point() + 
  scale_x_continuous(name = "X Axis", limits = c(-3, 3), breaks = seq(-3, 3, 1)) +
  scale_y_continuous(name = "Y Axis", limits = c(-3, 3), breaks = seq(-3, 3, 1))
```

## Customizing Themes

Themes control the non-data elements of your plot, such as the background, grid lines, and text. You can customize themes using the `theme()` function or apply pre-built themes like `theme_minimal()`, `theme_classic()`, etc.

```{r}
# Customize theme
ggplot(data, aes(x = x, y = y)) + 
  geom_point() + 
  theme_minimal() +
  theme(
    axis.title.x = element_text(size = 14, face = "bold"),
    axis.title.y = element_text(size = 14, face = "bold"),
    plot.title = element_text(size = 16, face = "bold", hjust = 0.5)
  ) +
  ggtitle("Customized ggplot2 Plot")
```

## Putting It All Together

Here is a complete example that combines all the elements discussed above:

```{r}
# Complete example
ggplot(data, aes(x = x, y = y)) + 
  geom_point(color = "blue", size = 3, alpha = 0.6) + 
  scale_x_continuous(name = "X Axis", limits = c(-3, 3), breaks = seq(-3, 3, 1)) +
  scale_y_continuous(name = "Y Axis", limits = c(-3, 3), breaks = seq(-3, 3, 1)) +
  theme_minimal() +
  theme(
    axis.title.x = element_text(size = 14, face = "bold"),
    axis.title.y = element_text(size = 14, face = "bold"),
    plot.title = element_text(size = 16, face = "bold", hjust = 0.5)
  ) +
  ggtitle("Complete ggplot2 Example")
```

By understanding and utilizing the grammar of graphics in `ggplot2`, you can create a wide variety of visualizations to effectively communicate your data insights.

To learn more about visualizing data with `ggplot2`, refer to our [Data Visualization with ggplot2](https://github.com/ELIXIREstonia/2024-10-09-R-visualisation) course.