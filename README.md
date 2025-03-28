# vplot 1.0
vplot is a wrapper for GNU Plot (gnuplot_i). The source of `gnuplot_i` I have downloaded from [this link](http://ndevilla.free.fr/gnuplot/). Files listed on gnuplot_i are taken from downloaded sources, including the license file.

# Dependecies
First, you need to install the `gnuplot` library.

On MacOS, you can install it using `brew`:
```bash
brew install gnuplot
```

# Get started

Install the library:
```bash
v install --git https://github.com/hungrybluedev/vplot
```

Import `vplot` library:
```v
import vplot
```

Use the above if you installed it through the Github repository link.

Declare a new Plot object:
```v
mut p1 := vplot.new()
```

Set a style and plot a slope of this function `y=ax+b`, where `a = 2` and `b = 0` and title `y=2x`. Also set label of X axis (`x`) and for Y axis (`2x`). 
```v
p1.style(vplot.style_linespoints)
p1.label_x(`x`)
p1.label_y(`y`)
p1.plot_slope(2.0)
```
Whenever you start a new plot session, you should closed it once you are done with it. But, in this simple example, you would not be able to see the output. To be able to see the output, we are going to call `os.input()` function in order to wait for any key to be pressed before closeing the plot session.
```v
	os.input('Press any key ...')
	p1.close()
```

# Change log:
- Removed all examples and moved to [vplot-playground](https://github.com/erdetn/vplot-playground/)
- Adding support for multiplots (similar to subplots in GNU Octave). Check example [multiplot.v](https://github.com/erdetn/vplot-playground/blob/main/multiplot.v)

# Documentation
| Function | Description |
| --- | ----------- |
| `vplot.new_plot` | Creates and returns new `Plot` object. |
| `vplot.Plot.close()` | Closes the plot sessions and kills corresponding PID.  |
| `vplot.Plot.command(command string)` | Executes a **GNU Plot** command |
| `vplot.Plot.commands(commands []string)` | Executes an array od **GNU Plot** commands |
| `vplot.Plot.style(style string)` | Sets the plot style. Check [Plot styles](#plot-styles). |
| `vplot.Plot.label_x(label string)` | Sets the label of X axis. |
| `vplot.Plot.label_y(label string)` | Sets the label of Y axis. |
| `vplot.Plot.reset()` | New plot erases the previous plot(s). |
| `vplot.Plot.plot(d[]f64, string)?` | Plots an array of `f64` data. It returns an error if the input array is empty. The second argument is the title of this plot. |
| `vplot.Plot.plot2(x []f64, y []f64, title string)` | Plots a pair of data from two arrays of `[]f64` data type. It returns an error if there is mismatch on length between two input arrays, or one of them is an empty array. The second argument is the title of this plot. |
| `vplot.Plot.plot_slope(a f64, b f64, title string)` | Plots a slop function `y = a*x + b`, where `a` and `b`, are the first and second argument. The third argument is the title of this function. |
| `vplot.Plot.plot_equation(equation string, title string)` | As per **gnuplot_i** documentations, this plots out a curve of given equation. The general form of the equation is y=f(x), you only provide the f(x) side of the equation. | 
| `vplot.write_x_csv(filename string, d []f64, title string)` | Writes a CSV file of a given array of `f64`. It return true/false if it failed or not to write the CSV file, otherwise, it returns an error if the given array is empty.|


# Plot styles

- `vplot.style_lines`
- `vplot.style_points`
- `vplot.style_linespoints`
- `vplot.style_impulses`
- `vplot.style_dots`
- `vplot.style_steps`
- `vplot.style_errorbars`
- `vplot.style_boxes`
- `vplot.style_boxeserrorbars`

# Tested functions

- [x] `new`
- [x] `Plot.close()`
- [x] `Plot.style(string)`
- [x] `Plot.plot_slope(f64, f64, string)`
- [x] `Plot.plot_equation(string, string)`
- [x] `Plot.reset()`
- [x] `Plot.enable_multiplot(Multiplotter)`
- [x] `Plot.disable_multiplot()`
- [x] `Plot.command(string)`
- [x] `Plot.commands([]string)` 
- [x] `Plot.plot2d([]f64, []f64, string)`
- [x] `Plot.plot([]f64, string)`
- [x] `Plot.label_x(string)`
- [x] `Plot.label_y(string)`
- [x] `vplot.write_x_csv(string, []f64, string)`
- [x] `vplot.write_xy_csv(string, []f64, []f64, string)`
- [x] `vplot.write_csv(string, []f64, []f64, string)`
- [x] `vplot.PlotSession{}`
- [x] `vplot.plotter(PlotSession)`


