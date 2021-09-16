## Export Troubleshooting:
1. Comment out the `%%capture` line in the cell that actually runs the exporting. Towards the bottom of the whole thing you might find something like an error message that may give you a clue as to what is going wrong. Likely it will be a LaTeX issue and say something about adding a missing `$`. 

2. If there is a space in your filename, try renaming and remove the space. In general, coding languages do not like spaces in filenames. I made the export script work fairly well with spaces, but it sometimes still causes issues.

3. Check images are all inserted with `Image(...)`. 

  a. If any images were previously inserted like `![](https://drive.google.com/uc?export=view&id=...)` it may be necessary to COPY ALL WORK into a new notebook.

4. LaTeX issues -- See below for LaTeX specific tips.

<br>

## LaTeX
The way Jupyter/Colab interprets markdown cells is slightly different to how the LaTeX compiler reads them, and unfortunately for us, the Jupyter/Colab interpreter is smarter than the LaTeX one, which means that even though things look great in the notebook, they might fail while exporting. 
So far, the things I have found to cause issues are:
* Spaces inside of `$` signs... e.g. `$ 50\pm10 $` won't compile, but `$50\pm10$` will. 
* Opening and closing many `$latex$` sections in one sentence seems to cause issues sometimes... e.g. avoid things like `$10\pm$5+$\mu$=40$\pm7$E$10$`
* If you use are using something like `\begin{align} ... \end{align`} (which defines a LaTeX enclosure) then you should NOT use `$` signs as well.
