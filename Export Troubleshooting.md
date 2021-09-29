## Export Troubleshooting:
1. Comment out the `%%capture` line in the cell that actually runs the exporting. Towards the bottom of the whole thing you might find something like an error message that may give you a clue as to what is going wrong. Likely it will be a LaTeX issue and say something about adding a missing `$`. 

2. Do a quick check that images are all inserted with `Image(...)`. 

3. Do a quick check of common LaTeX issues (often shows an error like `! Missing $ inserted.`) see below.

4. **Make a new `.ipynb` file and copy across cells a few at a time, making sure you can export the new `.ipynb` as you go.** Either you will be able to identify which cell is actually causing the problem, or you will get all the way to the end and it will continue to export in which case the problem is fixed! 
    (Just copying everything to a new notebook has been the solution for a few people this year, so I think Colab may have added some sort of history to files which can screw up the export process...)


<br>

## LaTeX
The way Jupyter/Colab interprets markdown cells is slightly different to how the LaTeX compiler reads them, and unfortunately for us, the Jupyter/Colab interpreter is smarter than the LaTeX one, which means that even though things look great in the notebook, they might fail while exporting. 
Some just do not render correctly:
* Inline text with a space at the end (e.g. `$5.0 $`). Will render as LaTeX in colab, but as regular text including "$" in export

Some cause the export to crash:
* Empty LaTeX (e.g. `$$` or `$$$$`). Will show up as empty space in Colab, but causes export to crash with `! Missing $ inserted.`
* Numbers directly after a closing `$` without a space first (e.g. `$10\pm$5`). Will render in Colab, but causes export to crash with `! Missing $ inserted.`
* Using `$` inside of a `\begin{equation}...` style LaTeX. Probably will not render correctly in Colab, and can cause a variety of export issues. Just stick to the `$1=1$` or `$$1=1$$` style LaTeX.
