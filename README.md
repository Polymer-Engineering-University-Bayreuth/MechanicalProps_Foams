# Script to calculate mechanical properties of foams (efficiency of absorption $\eta(\epsilon)$, compression modulus, work of compression, onset of plasticity, etc) from a strain-stress curve ($\sigma$ as a function of $\epsilon$). 

# The effficiency of absorption is calculated using the following expression:

#    $ \eta(\epsilon) = \frac{ \int_0^{\epsilon}{\sigma(\epsilon')d\epsilon'}}{{\sigma(\epsilon)}} $


## Input:

NOTE: your stress-strain curves must have epsilon (= strain) in percentage and sigma (= stress) in MPa units.

- txt file (space separated) or .csv file (comma separated, with or without a header) with two columns. First column = $\epsilon$, second column = $\sigma$ 
   
   OR
   
   
- excel file (.xls or .xlsx) with worksheets containing 2 columns (First column = $\epsilon$, second column = $\sigma$). You will need to provide the names of all worksheets you want to analyse.

   OR
   

- folder with excel OR txt OR csv files, each file following the specification above.

TIP: Check the files and folders provided with this script (file 'inputs.zip') to learn about their format!

### Requirements: Install the libraries "pandas, matplotlib, scipy, numpy, xlrd and openpyxl"
- You can do it from inside the Jupyter Notebook by executing "!pip install numpy scipy pandas matplotlib xlrd openpyxl" (without double quotes!)


## Outputs:
   NOTE: In all outputs, epsilon has fractionary units (not percentage units!).
  - Figure named "output_filename_sheetname.png" with the original stress-strain curve and the following calculated parameters: The efficiency of energy absorption $\eta(\epsilon)$ curve and $\eta_{max}$, work of compression ($W_{comp}$), epsilon where the densification starts ($\epsilon_{D}$), epsilon where the elastic region ends ($\epsilon_{pl}$) and corresponding sigma ($\sigma_{pl}$), Young's (or Compression) Modulus ($E^*$), the curve of $d\sigma/d\epsilon$ versus $\epsilon$ and the slope of the linear fit of the plateau region. The values of $\epsilon_{D}$ and $\epsilon_{pl}$ shown in the title of the upper subplot of the output figure, as well as shown inside the generated txt files did use the "zero-$\epsilon$" correction, which assumes that $\epsilon$ starts to be counted from the intersection of the tangent line at the elastic region (red line in the lower subplot of the output figure) and the horizontal axis (see below the parameter $\epsilon_0$ in the lower subplot of the output figure). Notice that $\epsilon_{pl}$ and $\sigma_{pl}$ (red circle in the lower subplot of the output figure) were plotted without this $\epsilon_0$ correction. $W_{comp}$ was calculated without this correction. 
  - A two-column .txt file named "eta_filename_sheetname.txt" with the $\eta(\epsilon)$ curve (first column = $\epsilon$, second column = efficiency or $\eta$).
  - If multiple files (from a given input folder) are treated, additional txt files with the different properties (one property per file) are generated. The files are named: Sigma_Plateau.txt, Slope_Plateau.txt, W_comp.txt, Epsilon_Densification.txt, Compression_Modulus.txt, Epsilon_Plateau.txt and Eta_max.txt. In each file, the average and standard deviation of all worksheets of a given input file are provided (in case of csv or txt files, the standard deviation is zero). A csv file named General_statistics.csv is also generated, where all averages and standard deviations of all calculated properties of all input files are compared.
  
## Online tutorial: [Click here to watch the video](https://mms.uni-bayreuth.de/Panopto/Pages/Viewer.aspx?id=2e1e92bd-504f-49f6-9d90-b068007446bf)
  
##### Script written by Rodrigo Q. de Albuquerque @11July2022 (experimental collaborators: Du lan, Johannes Meuchelboeck), University of Bayreuth, Germany
