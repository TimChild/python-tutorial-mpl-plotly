## Export Troubleshooting:
1. Comment out the `%%capture` line in the cell that actually runs the exporting. Towards the bottom of the whole thing you might find something like an error message that may give you a clue as to what is going wrong. Likely it will be a LaTeX issue and say something about adding a missing `$`. 

2. Check images are all inserted with `Image(...)`. 

    a. If any images were previously inserted like `![](https://drive.google.com/uc?export=view&id=...)` it may be necessary to COPY ALL WORK into a new notebook because some information gets stored in the background of a `.ipynb` file, and I have seen at least 1 case of this causing problems even once the offending line is removed.

3. LaTeX issues (often shows an error like `! Missing $ inserted.`) -- See below for LaTeX specific tips.

4. Make a new `.ipynb` file and copy across cells a few at a time, making sure you can export the new `.ipynb` as you go. That will help narrow down which cell has a problem if it has been difficult to find so far. 

<br>

## LaTeX
The way Jupyter/Colab interprets markdown cells is slightly different to how the LaTeX compiler reads them, and unfortunately for us, the Jupyter/Colab interpreter is smarter than the LaTeX one, which means that even though things look great in the notebook, they might fail while exporting. 
Some just do not render correctly:
* Inline text with a space at the end (e.g. `$5.0 $`). Will render as LaTeX in colab, but as regular text including "$" in export

Some cause the export to crash:
* Empty LaTeX (e.g. `$$` or `$$$$`). Will show up as empty space in Colab, but causes export to crash with `! Missing $ inserted.`
* Numbers directly after a closing `$` without a space first (e.g. `$10\pm$5`). Will render in Colab, but causes export to crash with `! Missing $ inserted.`
* Using `$` inside of a `\begin{equation}...` style LaTeX. Probably will not render correctly in Colab, and can cause a variety of export issues. Just stick to the `$1=1$` or `$$1=1$$` style LaTeX.
